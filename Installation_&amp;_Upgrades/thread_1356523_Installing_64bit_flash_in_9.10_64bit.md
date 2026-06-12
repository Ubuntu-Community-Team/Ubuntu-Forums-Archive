---
title: "Installing 64bit flash in 9.10 64bit"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by GuitarJim1987 on 2009-12-16
Hi everyone

I am having trouble installing the 64bit version of flash in 9.10 64 bit. I have been following the instructions [here]("http://profarius.com/content/64bit-java-flash-deathroll") however I'm stuck at the last little bit:

## As User
# Unpack flash
tar zxf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
# Create plugins directory if it doesn't exist
mkdir ~/.mozilla/plugins
# Move flash to plugins directory
mv libflashplayer.so ~/.mozilla/plugins/

When I type those commands the terminal returns an error stating it couldn't find the file which is obvious and if I try to copy straight into the plugins folder it won't let me due to root privileges required.

I have the libflashplayer.so in the 'downloads' folder and I need to move it to /usr/lib64/mozilla/plugins. Can anybody tell me how to do so please?

Many thanks.

---

### Post by darkod on 2009-12-16
If you have it already unpacked (if it's still packed as .tar.gz right-click, open with archive manager, and extract), just copy it in your home folder in .mozilla/plugins. There should be no permission errors, you are copying into your home folder, not in /usr.
Note: .mozilla is hidden folder, when you open your home folder press Ctrl + H to show hidden folders. Do the same to hide them again.

---

### Post by phillw on 2009-12-16
There was an update for 64 bit released on 8th Dec.

-->  [http://ubuntuforums.org/showthread.php?t=1352947](http://ubuntuforums.org/showthread.php?t=1352947)

(That has instructions for both 32 & 64 Bit)

Regards,

Phill.

---

### Post by hoboy on 2009-12-16
I was having problem with it I followed this link, that solved my problem.

[http://www.sucka.net/2009/07/ubuntu-9-04-flash-10-0-32-18-x86_64/comment-page-1/](http://www.sucka.net/2009/07/ubuntu-9-04-flash-10-0-32-18-x86_64/comment-page-1/)

---

