---
title: "[SOLVED] Cannot open any website on Firefox if TOR is enabled"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by al.adab on 2008-04-11
hello,

I'm on Ubuntu Gutsy + Firefox/2.0.0.13. The following is what I did to install TOR + Privoxy. When Tor is enabled on Firefox, I cannot reach any website. I tried to install FoxyProxy, but didn't get anywhere (probably because I don't know how to configure it). Could anyone please advise. Thanks. 

1) sudo apt-get install tor
2) sudo apt-get install privoxy
3) sudo nano /etc/privoxy/config
4) add forward-socks4a / localhost:9050 . to the file /etc/privoxy/config. Here's what the end part of my file looks like this:

# the exit option on the File menu).
#
#close-button-minimizes 1

# The "hide-console" option is specific to the MS-Win console version
# of Privoxy. If this option is used, Privoxy will disconnect from
# and hide the command console.
#
#hide-console

#forward-socks4a / localhost:9050 .


5) modify the following part (same file, /etc/privoxy/config) so that it looks like this:

# The available debug levels are:
#
# debug 1 # show each GET/POST/CONNECT request
# debug 2 # show each connection status
# debug 4 # show I/O status
# debug 8 # show header parsing
# debug 16 # log all data into the logfile
# debug 32 # debug force feature
# debug 64 # debug regular expression filter
# debug 128 # debug fast redirects
# debug 256 # debug GIF de-animation
# debug 512 # Common Log Format
# debug 1024 # debug kill pop-ups
# debug 2048 # CGI user interface
# debug 4096 # Startup banner and warnings
# debug 8192 # Errors - *we highly recommended enabling this*
#

6) add "SafeLogging 1" to the file /etc/tor/torrc. The end part of my file looks like this:

## users will be told that those destinations are down.
##
#ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
#ExitPolicy accept *:119 # accept nntp as well as default exit policy
#ExitPolicy reject *:* # no exits allowed
#SafeLogging 1

7) run sudo /etc/init.d/tor start. Result:

sudo /etc/init.d/tor start
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
done.

run sudo /etc/init.d/privoxy start. Result:

~$ sudo /etc/init.d/privoxy start
Starting filtering proxy server: privoxy.

9) run netstat -a | grep 9050 (supposedly to check that everything's fine. Result:

~$ sudo /etc/init.d/privoxy start
Starting filtering proxy server: privoxy.
daniel@al:~$ netstat -a | grep 9050
tcp 0 0 localhost:9050 *:* LISTEN

10) Go to Firefox>Edit>Preferences>Advanced>Settings and set it according to the screenshot here attached.

11) Go to Firefox>Tools>AddsOn>Tor Button>Preferences>Use Custom Proxy Settings

12) Install Tor Proxy Net toolbar.

13) Restart the computer

14) test Firefox with "Tor Enabled" and "Tor Disabled" on the following websites (test's result):

a) [https://torcheck.xenobite.eu/](https://torcheck.xenobite.eu/) (message given on both "Enabled" and "Disabled": Your IP is NOT identified to be a Tor-EXIT. So you are NOT using Tor to reach the web!

b) [http://whatismyip.com](http://whatismyip.com) (IP address detected is the same on both "Enabled" and "Disabled".

Also my assumption is that TOR Enabled should prevent (almost) anyone from detecting my IP address and TOR Proxy Net is specifically to surf blocked websites or the like. Is this correct?

Thanks for taking the time to read this. Hope there's a solution.

---

### Post by al.adab on 2008-04-11
corrigendum:

a) [https://torcheck.xenobite.eu/](https://torcheck.xenobite.eu/) (message given on  "Disabled": Your IP is NOT identified to be a Tor-EXIT. So you are NOT using Tor to reach the web!

b) [http://whatismyip.com](http://whatismyip.com) (IP address detected  "Disabled").

---

### Post by al.adab on 2008-04-11
Update: I've uninstalled + reinstalled FoxyProxy (automatically set on "use proxies based on their predefined patterns). Result:

1) I can now navigate with Tor enabled on Firefox
2) if I check my IP at [http://whatismyip.com/](http://whatismyip.com/) I get two different IP addresses according to whether or not Tor is enabled
3) if I check [https://torcheck.xenobite.eu](https://torcheck.xenobite.eu) I get the following message:
Your IP is NOT identified to be a Tor-EXIT.
So you are NOT using Tor to reach the web!
4) if I check the "Tor Detector" (see [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)) I get the following message:
Sorry. You are (probably) not using Tor.

---

### Post by al.adab on 2008-04-11
Further update:

1) now [http://whatismyip.com/](http://whatismyip.com/) always detects the same IP address, regardless of whether or not Tor is enabled on Firefox
2) the IP address detected at [http://whatismyip.com/](http://whatismyip.com/) is the same [https://torcheck.xenobite.eu](https://torcheck.xenobite.eu) detects

---

### Post by al.adab on 2008-04-13
please see [http://ubuntuforums.org/showthread.php?t=751230&highlight=TOR](http://ubuntuforums.org/showthread.php?t=751230&highlight=TOR)

---

