---
title: "Dual boot unsuccessful"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by timstone on 2010-03-21
I just downloaded and installed 9.10.  I have it installed on a separate drive than my windows OS.  When asked to reboot I did so and instead of giving me a GRUB loader I was left with the Windows loader which wasn't a problem because Ubuntu shows up on the list.  But when I went to load Ubuntu it wouldn't load at all.  It gave me an error about not having the disk and said that wubi.mbr or whatever that file is called was missing.  I have no clue what to do....my cd burner is broken so I can't burn these files to disc and when running wubi.exe I tried to run the demo and install that way but the demo never starts up at all.

Can anyone help me out?

---

### Post by derekeverett on 2010-03-21
I'm not clear about something. Were you using Wubi for the initial Ubuntu install? 

If you were then it should install it inside your Windows partition. And the Windows bootloader would be the one you use, not grub.

---

### Post by timstone on 2010-03-21
Ok well that might be the problem.....I told it to install on a separate drive than where my windows install was at....which is how I want it done...can I not do this with 9.10?  I didn't see any other way to install since the demo never started up....

---

### Post by derekeverett on 2010-03-21
Wubi installs within Windows.. which has it's advantages. One of the big ones is that you can uninstall within the Control Panel add/remove programs.

Dual booting in a more traditional way will allow you to choose your partitions and give you the grub boot loader. Which version of Windows are you running?

---

### Post by raymondh on 2010-03-21
> **timstone said:**
> Ok well that might be the problem.....I told it to install on a separate drive than where my windows install was at....which is how I want it done...can I not do this with 9.10?  I didn't see any other way to install since the demo never started up....

You can install it to the other hd.

First ... to clarify ... did you do a wubi-install (i.e. was windows running when you installed ubuntu)?  If yes, _and you want to keep it that way_, see the [wubi-guid]("https://wiki.ubuntu.com/WubiGuide")e for possible solutions.  It may be dated but is still relevant.

If you want to install ubuntu in it's own partition or HD, post back and the forum can guide you.

- you might want to remove the wubi-ubuntu to simplify.
- have a tested/working back-up of your files


Best,

Raymond

---

### Post by timstone on 2010-03-21
I did install it within windows using wubi...I am using Windows 7 currently.  I'm downloading from another source right now.....hoping this one will work right.  I uninstalled what I had just installed and I'm hoping the demo/separate install will actually work on this one.

EDIT:  nope...download just finished and nothing has changed.  I click the demo/full install button and it asks me to restart.  I check restart now and then click next/finish and it just sits there.  Maybe it would just be easier if I installed an older copy without wubi and then upgraded.

---

### Post by raymondh on 2010-03-21
> **timstone said:**
> I did install it within windows using wubi...I am using Windows 7 currently.  I'm downloading from another source right now.....hoping this one will work right.  I uninstalled what I had just installed and I'm hoping the demo/separate install will actually work on this one.

are you going for another wubi-install or are you planning to install in it's own HD with it's own partition?

---

### Post by timstone on 2010-03-21
> **raymondh said:**
> are you going for another wubi-install or are you planning to install in it's own HD with it's own partition?

I'm downloading Jaunty currently.  I hope it doesn't have a wubi installer with it.  But yes that was my plan was to do install it on its on HD and it's own partition.

EDIT:  Ok...I'm done downloading for the night I think unless I can get a fast response here....I need an image file that does not have wubi...I just want to install the old way...the full install method with wubi is not working for me on 3 different versions.

---

### Post by timstone on 2010-03-22
Ok I'm not really sure why or how but instead of trying to install wubi to my 2nd hard drive I tried it on my windows drive and it worked fine.  Now that I'm actually in Ubuntu I want to get a clean install done to the 2nd hard drive and delete this wubi install.

---

### Post by bumanie on 2010-03-22
Wubi will only work from within windows - that is what it is designed to do - work within windows. If you are happy with the installation of wubi, it is possible to copy ubuntu to a separate drive/partition by looking at [this ]("http://lubi.sourceforge.net/lvpm.html") and [this]("http://lubi.sourceforge.net/lvpm.html") - it saves having to do a complete reinstallation. Of course a fresh installation to a separate hard drive won't hurt, just make sure you don't try that with wubi - that is not what wubi is meant for.

---

### Post by raymondh on 2010-03-22
All liveCD's (not alternate CD's) have the wubi function.  Probably, the reason you are doing a wubi-install is that your windows is open (live) when you load and the Ubuntu liveCD.   That tells Ubiquity (the ubuntu installer) that you want to do a wubi-install.

You can try to 'migrate' as Bumanie suggested.  Or, if you want to do a clean install, and after you delete the wubi-install :

*** I am assuming that the 2nd HD contains nothing and that you intend to use the second HD solely for Ubuntu.  If otherwise, post back and we can alter/modify this guide.**

1. From windows, defrag the 2nd HD.  2x if you have the time.
2. Exit and close windows.
3. Start-up your computer and access the quick boot menu.  Usually there is a key (F12, F2, ESC, DEL, etc.) that will stop the boot-up process and allow you to either access BIOS or, a quick bios menu.
-  whether in 'quick menu' or in actual BIOS, change the booting sequence so that the CD-drive will boot first before any hd
4. Load your liveCD in the CD Drive.
5. Continue the boot-up.  You should be booting into the liveCD and to what is known as a live session.  Play around in live session first to see how your computer reacts with Ubuntu (wifi, sound, etc).
6. When satisfied, continue and click on install.
7. In step 4 of the install process, there is a dropdown box on the upper right.  Using that dropdown box, select the 2nd HD.  You ought to notice that the visual (below, same window) will change to reflect the 2nd HD and its' contents/partitions, etc.  By selecting the 2nd HD, you are now telling the installer .... "hey ubiquity, I want you to install Ubuntu in the 2nd HD !! "
8. Continuing, you'll be given options on how to install.  In this guide/example, select "use the entire disc space".  Be careful .... using the entire disc space will erase and reformat said space.  If you have another OS there or a partition with a drive letter assigned in windows, you will lose it.  This is the reason why I wrote the assumption at the beginning of this post.
9. Continue with the install.  In step 7, there is an 'advanced' button (lower right).  If you click on it, it will show you where GRUB will install.  Chances are it will reflect the 1st HD.  That is because you have the first HD set to boot first in BIOS. *I am assuming that you have finally decided to use GRUB as your bootloader and, _from your other thread_, you no longer wish to retain the windows bootloader.*  My point here is that this is where you can choose which MBR (1st or 2nd HD)... or partition... to install GRUB.  If you still have the windows bootloader intact in the 1st HD, you can choose to install GRUB in the 2nd HD, effectively keeping windows bootloader original.  Just remember to change BIOS to set the 2nd HD to boot first.

**At any time before STEP 7 you do not feel comfortable, you can exit the install process.  After step 7, that's it!**  

Have a working/tested back-up of your files.

---

