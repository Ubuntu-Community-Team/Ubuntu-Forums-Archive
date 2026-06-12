---
title: "can't upgrade from 22.04 to 24.04.x, all security.ubuntu.com mirrors refuse HTTPS"
date: 2024-10-30
forum: Installation &amp; Upgrades
---

### Post by alessandro-s-ita on 2024-10-30
Hasn't worked for weeks, so let me try and ask for help here - apologies if it turns out to be something obvious....

If I try to update from the GUI I get an uninformative window telling me there's a generic error and I should try wired ethernet (I'm on wired 1Gbps ethernet straight to 1Gbps FTTH FritzBox 7590). No big deal, let's switch to command line.

apt update fails to contact security.ubuntu.com to update the nginx GPG key (some mirrors return 111, others get a timeout), so I get the GPG key via nginx, successfully put it into its place after passing it through gpg --dearmor. So far so good.
I retry apt update -- which now hangs at xenial-security InRelease and ultimately fails again, so I haven't really solved much.


I go through a number of attempts, such as:

 - is it IPV6? Nope, still fails even when editing /etc/gai.conf to uncomment the preference line to favor IPv4, and it also still fails using apt-get -o Acquire::ForceIPv4=true update instead of plain apt update
 - do I have computer-side firewalling on? Nope, iptables -L is clean
 - am I using DHCP on the computer I am trying to upgrade - no, IP in local LAN is fixed
 - can I reach any Ubuntu security mirrors via traceroute - find out I don't have the traceroute package, install it via apt install inetutils-traceroute [so, apt install does work] -and  yes, I can reach at least 185.125.190.82 in 44ms
 - is it my internet provider blocking Ubuntu security servers? doesn't seem to be, I can't get to xenial-security in security.ubuntu.com via browser through my work VPN as well (going through a different country) - but I'm doing that via a non-Ubuntu Linux system, so I'm unsure whether this test matters or otherwise
 - will the update work if I switch to HTTP in /etc/apt/sources.list? No, apt complains that such an update can't be done securely as the repo isn't signed


Barring other suggestions, I'll try moving the computer in the next days into a different place with a different network provider and see whether that also fails... thanks in advance for any ideas!

---

### Post by alessandro-s-ita on 2024-10-31
Well the issue kept manifesting even at a different place with a different network provider... which would suggest either nobody could upgrade any Ubuntu (but there was no major warning anywhere on the 'net, so that looked extremely unlikely), or there was something out of whack on the local computer...


Turns out my 10yo whiz kid had added extra lines in /etc/apt/sources.list because he needed some earlier OpenSSL libs (possibly for Dolphin or some other emulation software) and then forgot those there.

When I showed him the post he said 'Ah - now I remember. Sorry; I know how to fix that' , removed the additional lines from sources.list and voila - some short time later the upgrade had completed.

Case closed :)

---

