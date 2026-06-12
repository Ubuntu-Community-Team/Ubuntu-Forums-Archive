---
title: "Please help dual boot problem"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Aterruit on 2010-06-08
Ok, I am an avid ubuntu fan, and have been using ubuntu since 8.something. However, I never figured out a way to run WOW from Ubuntu, so I switched to winblows 7. I had my hard drive partitioned with vista, and 7 on it.  (it's a long story) I was waiting for my new Ubuntu 10.4 cd to come in the mail, but i grew impatient and installed it on my pc. When I did I was careful not to install it over my Windows 7 partition. Infact, it made a new partition and installed it. So then i had 7, Ubuntu, and vista on my laptop. I formatted the vista partition and now it's blank. My problem is, when i start my computer, Windows 7 is no long an option in my boot menu. WTF happened? and can i get it back? All the files are still there, the partition is still there, from what I understand the whole OS is still there, but it's not on the Boot menu. Can someone please help fix this? I'm kind of a noob to ubuntu, I'm familiar with terminal and such. but if something is a bit out of my grasp i'll let you know. THANK YOU ALL SO MUCH FOR YOU TIME AND HELP

(ps, if someone could  walk me through how to install and play WOW on linux flawlessly, that would work too.)

---

### Post by bcbc on 2010-06-08
I can't help you with the WOW - although I've seen comments that you can play it on Ubuntu.

But I'll try and comment on your booting problems. When you install a newer version of windows (in this case 7) on a disk with an older version of windows (vista), windows adds the boot menu files on the old partition. So most likely, when you wiped vista, you wiped these files (unless you took special precautions when you installed win7). You can read all about it here: [http://www.multibooters.co.uk/system.html](http://www.multibooters.co.uk/system.html)

So I figure you'll need to use your win7 dvd to repair your win7 install. Try this [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Also make sure you set your win7 partition to be the active partition. 

And have your ubuntu live cd handy to reinstall the grub bootloader back to the MBR after the windows is repaired. see here (chapter 13) if you need help [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Aterruit on 2010-06-08
Thanks Man I appreciate it. I will let you know if anything progresses. My windows copy was a burnt one, so  now i have to dig that up. I'll keep you posted. thanks.

---

### Post by Aterruit on 2010-06-08
Is it possible for my to do this from a file in the .iso file? Because, that's how I got my windows.

---

### Post by Aterruit on 2010-06-08
Is it possible for me to use WINE to run DOS so i  can run the bootrec.exe program?

---

### Post by bcbc on 2010-06-08
> **Aterruit said:**
> Is it possible for me to use WINE to run DOS so i  can run the bootrec.exe program?

I'm sorry I can't help you there. Not sure how you installed windows 7 from a .iso either. Do you not have a dvd/cd drive you can burn a repair cd from?

---

### Post by Aterruit on 2010-06-08
Um no. I'll have to burn another one tomorrow.

---

### Post by Aterruit on 2010-06-10
OK So i've got my WIN 7 cd, and i am working on doing all the things you told me to do. yet i am still having problems. Is it possible for me to remove ubuntu from my MBR entirley so that my WIN 7 comes up. Then i can go back and re-install Ubuntu into my MBR.

---

### Post by darkod on 2010-06-10
It's best to download and run the boot info script, and then post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That way we can see what is where exactly.

If grub2 can't locate win7, usually there is problem with the win7 boot files and in that case just restoring the MBR won't help. In fact, sometimes windows can't even repair its own boot files. Lets see what is where first with the help of the script.

---

