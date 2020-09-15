# The Cod Caper - TryHackMe

# NOT FINISHED

[Link to CTF](https://tryhackme.com/room/thecodcaper)

A simple guide to completing The Cod Caper.

## Host enumeration

1. We can use nmap to find the number of open ports: `nmap -sV BOX_IP`. There is a SSH and HTTP port.
2. Nmap has a built-in script to find the HTTP title: `nmap --script http-title BOX_IP`. Alternatively, we can just visit `http://BOX_IP` in our browser to find the tab title.
3. We can look at the first nmap scan to find the versions (don't include the parenthesis)
4. The answer is `apache/VERSION_NUMBER`

## Web enumeration

1. Now it's time to find any userful directories on the server. Using gobuster, we would run the command `gobuster -w PATH_TO_WORDLIST -u http://BOX_IP`. However, we don't find anything interesting from this command. But since we know that the server is running PHP, we can try appending .php to the end of every gobuster request using `-x php` and running the command again. The recommended wordlist can be [found here](https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/Web-Content/big.txt). Once it finishes, we should see that it finds an interesting file `administrator.php`.


