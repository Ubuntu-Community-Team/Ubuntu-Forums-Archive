---
title: "flashplugin-nonfree doesn't work properly (U 7.10)"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by mhall on 2008-01-07
Hi, fellow Ubuntu users!

I've recently installed Ubuntu 7.10 (i386, 32-bit) on my Acer Aspire 5102WLMi. I had both 6.10 and 7.04 earlier, and in both of them the Flash plugin have worked properly. Now, on the other hand, everything is totally messed up. MySpace players will not load completely, all buttons will either be unclickable or flashing constantly. Almost the same goes for the YouTube player, and other flash stuff.

Is the new Flash plugin buggy, is the new Firefox buggy, or what might be the problem here?

Thank you on beforehand,
Martin

---

### Post by dannyboy79 on 2008-01-07
uninstall the synaptic version of flashplugin-nonfree and download the latest flash player from adobe's website. then unpack it, and place the libflashplayer.so within 

/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so

and you should be good to go. don't bother with the installer as it won't allow you to put the file within the folders, just copy the file to each of the folders after you extract the tarball. Also, this has been posted many many times as an FYI. the search feature in this forum is invalulable.

---

### Post by M0nk3yM4n on 2008-01-08
The thing is this should be done automatically. Why are simple things such as flash which is such a cornerstone of web browsing so hard to put on the newest version of Ubuntu? Isn't Ubuntu trying to reach a point where CLI is not "possible" but not necessary? I have been a faithful tried and tested Ubuntu user for a while but this rubs me in the wrong way.

---

### Post by dannyboy79 on 2008-01-08
sorry to hear that. it's a bug that I am sure will be worked out with Hardy and if it's not, we have a solution. Ubuntu is trying to become a user friendly desktop OS but it takes time of many people to get there. What you get with Ubuntu is FREE and although there are little issues here and there, it's awesome!

I have presented you the solution, hopefully you got it working.

---

### Post by werewolves on 2008-01-08
> **dannyboy79 said:**
> uninstall the synaptic version of flashplugin-nonfree and download the latest flash player from adobe's website. then unpack it, and place the libflashplayer.so within 

/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so

and you should be good to go. don't bother with the installer as it won't allow you to put the file within the folders, just copy the file to each of the folders after you extract the tarball. Also, this has been posted many many times as an FYI. the search feature in this forum is invalulable.

This did not work for me.  I can navigate to the directories indicated and see the libflashplayer.so file that I copied in, but Firefox is still not seeing it.

---

### Post by oldsoundguy on 2008-01-08
you have to INSTALL IT in Firefox.  Unlike WinDOZE, things are not totally automatic in Linux.
This guide is VERY helpful and is UPDATED on a regular basis.  (so book mark it and use it .. great to be able to open a terminal and just copy and paste the command lines!)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by ColdCanadian on 2008-01-08
> **dannyboy79 said:**
> uninstall the synaptic version of flashplugin-nonfree and download the latest flash player from adobe's website. then unpack it, and place the libflashplayer.so within 

/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so

and you should be good to go. don't bother with the installer as it won't allow you to put the file within the folders, just copy the file to each of the folders after you extract the tarball. Also, this has been posted many many times as an FYI. the search feature in this forum is invalulable.

I'm a complete newb, so bare with me. I tried to copy the files into the folders but it says 

"error while copying to /usr/lib/mozilla/plugins" You do not have permissions to write to this folder.

whats causing this and how do I fix this?

Thanks

---

### Post by dannyboy79 on 2008-01-08
you need to use "sudo" in the beginning of the command because that folder is owned by root. sudo gives you root privelages temporarily. sudo's password is the same as your's because you are in the admin group. good luck

---

### Post by dannyboy79 on 2008-01-08
> **oldsoundguy said:**
> you have to INSTALL IT in Firefox.  Unlike WinDOZE, things are not totally automatic in Linux.
This guide is VERY helpful and is UPDATED on a regular basis.  (so book mark it and use it .. great to be able to open a terminal and just copy and paste the command lines!)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

i didn't get the md5sum error, it just wasn't putting the files within the directories I told it to despite running the installer. so I just moved them there manually and all is well. at least that's on my Mythbuntu Gutsy distro. youtube galore, yeah!

---

### Post by Ludwix on 2008-01-08
I had the same problems with the synaptics version of the flash plugin.

This solved my problem:

Uninstall the plugin:
sudo apt-get remove flashplugin-nonfree

Download the deb package:
wget [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Install the downloaded package:
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb

Hope it helps

Greetz

---

### Post by benrboone on 2008-01-08
If you are using 64 bit,there is a fix for the 64 bit version of flash as well
take a look at this forum

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
the package you want for amd64 is flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb

I've used three different times to fix my friends computers

This will give you some warning about a package in the repositories that is better just ignore it and in stall it anyways

ps like stated above the problem lies with adobe changing the file which results in a new checksum this causes the flash to fell to install although it report success in the gui. The terminal output however does show failure

---

