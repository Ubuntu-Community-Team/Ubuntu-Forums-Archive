---
title: "Pl Help wth Netboot error &quot;Bad archive mirror error&quot;"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by fox_bat on 2007-06-20
Sometime back I used this wiki [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)  to install Ubuntu on my Toshiba Protege 3500 which doesnt have an CD nor floppy and all went well until I screwed up my laptop and needed to install Ubutu again using the netboot option. I used the same steps mentioned in the link above and did everything as described.

Plus I dont have any proxy whats so ever and my laptop was connected to the DSL router and netbbot via a windows machine using Tftpd32. This is how I had installed it the frist time a few months ago and all went well.

NOW however what happens is that all goes well till I get to the prompt 

Please enter the directory in which the mirror of the Ubuntu archive is located.

Ubuntu archive mirror directory:

in my case i treid to use many European based mirrors like ch.archives.ubuntu.com( and others that are listed)
and finally...

If you need to use a HTTP Proxy ... (left this one blank)

The official error returned is:
Bad archive mirror
The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.
I tried all mirrors as mentioned above and the same error :(
Does anyone have an idea of what the problem could be, or a possible alternate solution?

Thanks for the help

---

### Post by fox_bat on 2007-06-20
Well found the answer the wiki link and netboot was for Breezy and therefore couldnt find the files and bad archive error message. 

The answer is here [http://ubuntuforums.org/showthread.php?t=327597&highlight=netboot](http://ubuntuforums.org/showthread.php?t=327597&highlight=netboot)

---

### Post by flexus on 2007-07-30
Hi!
I have a Toshiba Portege 3440 CT and I am trying to install ubuntu via netboot. I get the exact same problem that you described. 

I know the laptop gets an ip from the windows machine bc I have an old still (barely) functionning installation of windows on it and I can acces the internet when I boot that. 

When I boot from LAN everything works fine to the point where I am supposed to choose a mirror. I have tried several mirrors all over the world and I get the same error you described. 

I checked out the thread you recommended, but it did not help. What specificly did you do to make it work?

thanks 

k

---

