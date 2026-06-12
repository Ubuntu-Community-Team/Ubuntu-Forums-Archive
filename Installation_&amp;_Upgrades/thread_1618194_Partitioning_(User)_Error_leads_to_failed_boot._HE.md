---
title: "Partitioning (User) Error leads to failed boot. HELP!"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by maincm on 2010-11-10
So, I'm a newbie. Just installed the newest version of Ubuntu and now my computer won't load at all. Please note: I'm a non-tech person, just tired of Windows XP and trying out the freesource as it's a great idea. 

Here's the situation: I have the newest release of Ubuntu running in dual mode with a constantly failing Windows XP. I installed with GRUB and had no issues, but wanted to have access to the Windows files from Ubuntu (it did a logical partition and I couldn't locate any of the Windows files), allocate more space to Ubuntu and make the dual mode more efficient. Last night, I read up on how to do these things, went to GParted to briefly look at how the partitioning process would work. I believed that I took no action, shut down, and now the computer won't boot. It brings up the HP load screen with the Boot Device Menu and ROM Based Setup but immediately goes to a black screen with a flashing white bar. I tried restoring my defaults in the BIOS and I tested the RAM and HDD, each failing to resolve my issue. I'm assuming that whatever I've done is keeping the computer from knowing where to boot from. Any ideas on how to resolve my problem? I'd really appreciate the help. Thanks.

Failed newbie searching for a passing grade.
-maincm

---

### Post by dino99 on 2010-11-10
[http://ubuntuforums.org/showpost.php?p=10098299&postcount=2](http://ubuntuforums.org/showpost.php?p=10098299&postcount=2)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by oldfred on 2010-11-10
If you have a full install your windows files should be easily accessible, just the name may be 200GB partition, if you did not label it. Even in wubi you can get to your windows partition from the file browser - Nautilus.

To see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by maincm on 2010-11-10
That does clear up my situation in accessing Windows from Ubuntu as well as the proper partitioning method. However, I still cannot boot my computer to complete either of these actions. When I turn the notebook on I get the screen that would allow me to access the BIOS and instead of moving to the screen that allows me the option to boot Windows XP or Ubuntu it's a black screen with the flashing white dash. How do I resolve this issue? Thanks for your responses, just a little bit more help needed.

---

### Post by oldfred on 2010-11-10
We need the boot info script results.txt posted. You can run it from a liveCD.

If you installed with wubi you are running Ubuntu from a file inside the windows NTFS partition. If XP is failing then the Ubuntu may also. One of the advantages of separate partitons, although more complicated to set up initially.

---

### Post by devil89 on 2010-11-10
[SIZE=4]I also had almost the same problem. But I have messed my Windows 7 Home Premium 64-bit, along with all stuff in my hdd.
And now i could not reinstall my original windows 7 [/SIZE]

---

### Post by maincm on 2010-11-11
Thank you all for your help. I took the easy out and created an Ubuntu LiveCD starting over from square one (with all the proper partitioning). I already had everything backed up and ready to move, so I just ditched Windows altogether. Thanks again!

---

