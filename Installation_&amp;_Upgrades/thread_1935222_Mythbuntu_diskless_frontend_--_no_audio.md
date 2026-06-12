---
title: "Mythbuntu diskless frontend -- no audio"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by rage_311 on 2012-03-03
Another day, another linux adventure...

So, on a side note, I ran across this linux powered LAN gaming house article recently... [http://www.linuxjournal.com/content/linux-powered-lan-gaming-house](http://www.linuxjournal.com/content/linux-powered-lan-gaming-house)
And it gave me the idea to convert my existing Mythbuntu frontends from a traditional local-booting installation to a network booting OS/install.  So, I found a nice guide for Mythbuntu specifically that walked me through achieving my desired setup ([https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless](https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless)) -- so far, so good.  I used my local Ubuntu 10.04.3 server to install the DHCP, TFTP, and LTSP packages and my client machine can boot from it just fine.  The only problem that I've seen on the client so far is the lack of audio.  There's nothing alsa-related that's running, Mythtv can't see any actual audio devices, and alsamixer is unavailable.  The client machine that is my first guinea pig is an i3-540 on an Asus H55 board with onboard HDMI -- which is the same connector that I'd like to output my audio on.  

The question I pose is... where do I need to start with the investigation of the audio situation?  In normal Mythbuntu installs, it has just been installed/configured for me and I haven't really had to deal with this.  By the way, lspci does list my onboard Intel audio device... but I'm not sure where to go from there.

Please let me know if I can provide any additional, relevant info in order to get this resolved.  Also, if there is information that will also pertain to my 2nd frontend (an AMD Athlon X2 machine), please let me know.  Thanks in advance.

---

