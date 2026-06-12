---
title: "Database locked, etc."
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by darkthunderfx on 2008-02-17
I just installed the latest Kubuntu. First thing I go to do is run the updates and enable restricted drivers to get my wireless card to work. I get an error while trying to enable the firware for my card saying 'Database locked' another process is using the packaging system database... etc. When I try to continue the program crashes and I get this.


(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47871952243152 (LWP 21788)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00002b8a0dff7765 in raise () from /lib/libc.so.6
#6  0x00002b8a0dff91c0 in abort () from /lib/libc.so.6
#7  0x00002b8a0d8f17b4 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#8  0x00002b8a0d8ef746 in ?? () from /usr/lib/libstdc++.so.6
#9  0x00002b8a0d8ef773 in std::terminate () from /usr/lib/libstdc++.so.6
#10 0x00002b8a0d8ef85a in __cxa_throw () from /usr/lib/libstdc++.so.6
#11 0x0000000000438b11 in ?? ()
#12 0x0000000000439184 in ?? ()
#13 0x00000000004396fd in ?? ()
#14 0x000000000041bc7c in ?? ()
#15 0x000000000041b209 in ?? ()
#16 0x00002b8a0dfe3b44 in __libc_start_main () from /lib/libc.so.6
#17 0x000000000041afb9 in ?? ()
#18 0x00007fffa3a9b4a8 in ?? ()
#19 0x0000000000000000 in ?? ()

I get the same thing when I try to run add/remove programs. I've seen other people post stuff on this when I looked around, but for them all they had to do was  sudo apt-get install -f. When I try this I get an error saying I need superuser privileges.

Any help is appreciated.

---

### Post by calman on 2008-02-17
You get the database locked message because you already have a process trying to install packages with aptitude.  If you have aptitude open, close it.  Otherwise, close all other programs that are open.  If you have to, go to the system monitor and kill the 'aptitude' process if it's there.  if you're using the 'sudo' command, you shouldn't need superuser privileges...don't know why you get that 

Even if you get past this error, you're going to still have trouble, because in order to install restricted drivers, you need internet access.  This has been a huge problem for a lot of users, because you can't install a driver over the internet for a device that connects to the internet.....so, unless by some miracle it works after you get by the database locked error, you have 3 choices:

1.  get a long ethernet cord and wire up your computer, then let the restricted drivers manager work its magic.
2.  get another wireless card (NOT linksys)
3.  install the drivers on your own.  can be very painful, i can help you through this if you need me to

---

### Post by darkthunderfx on 2008-02-17
Thanks for the quick response.

With your suggestion, I am now using a long cat5 cable and am able to get a connection this way. While following the directions at [http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps) I run in to a brick wall with the first line on step 11, 'cd ~/ndiswrapper'. This is what happens.

user@user-laptop:~$ cd ~/ndiswrapper
bash: cd: /home/user/ndiswrapper: Not a directory

What am I doing wrong? The file is there, it appears?

---

### Post by calman on 2008-02-17
darkthunder-

alright, so ~ means the home directory.  so, if your login name is "tux" your home folder is /home/tux.  

you made a folder called niswrapper in step 10, in your home folder.  did you get any errors when doing the mkdir command?  what's weird is that it's looking in /home/user instead of /home/<yourloginname>.  unless, of course, your login name is 'user'?

a warning about ndiswrapper:  it's a great piece of software, very useful and all, but it's definitely a last resort.  have you tried, since you got your ethernet internet connection working, going back to restricted drivers manager and enabling your wireless card?  this will download the best drivers (much better than the dreaded ndiswrapper) and you'll be up and running, without your cat5, in no time.

---

### Post by darkthunderfx on 2008-02-17
I once saw the "restricted drivers manager" next to the clock, but even after a restart I cannot find it.

How else may I find it?

---

### Post by calman on 2008-02-17
system > administration > restricted drivers manager

the biggest improvement in the ubuntu distro so far...you're going to love your life when you see how easy it is.  just check the box and let me know how it goes.

---

### Post by darkthunderfx on 2008-02-17
I don't find that option. I'm using Kubuntu, in case you didn't know. I can take a screenshot if you'd like.

---

### Post by calman on 2008-02-17
That's right, i forgot...i think the command is "restricted-manager" try that in the terminal.

---

### Post by darkthunderfx on 2008-02-17
Great, it appears to work just fine. Will this run at 54mps? I've read somewhere fwcutter only goes at 11.

Only problem I have with it is Pidgin won't connect with the wireless. Firefox works fine though. Any suggestions on how to make Pidgin connect?

---

### Post by calman on 2008-02-17
It should run at maximum speed, not really sure though, I know ndiswrapper is slow and i would think fwcutter is too.  It didn't give you fwcutter did it?

That's weird that pidgin doesn't connect, probably a whole new issue.  I would probably reboot, if that doesn't work I'd stat googling or start a new topic, but I have never had a problem like that.

---

### Post by darkthunderfx on 2008-02-17
Once I restarted I have ran in to a few more issues. The restricted drivers manager appears to still have the devices enabled with the firmware, However, Kwifimanager and wireless assistant do not detect the wireless card until I go in to restricted drivers manager and disable, and then re-enable the device and it's firmware. Any ideas on how to avoid doing this?

---

### Post by calman on 2008-02-17
Is your wireless card integrated into the motherboard?  Or is it USB/PCI/something else?

If it's integrated, go into your BIOS and make sure that it will always be turned on during the boot sequence.  That would explain why you have to disable/renable it,this is essentially waking it up because it is off.

---

