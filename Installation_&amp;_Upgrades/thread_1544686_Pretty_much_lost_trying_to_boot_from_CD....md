---
title: "Pretty much lost trying to boot from CD..."
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by youradhere4222 on 2010-08-02
As a back story, my Thinkpad had two partitions on it; one with Windows Vista and one with Windows 7. But it can't find the boot files, and thus isn't starting up (I'm getting a remove media or other devices error). 

So I'm just trying to get it working by trying to download the Ubuntu ISO on another computer, burning it to a disk and then booting it up on my Thinkpad.

I downloaded the 32-bit ISO of Ubuntu. It's ubuntu-10.04-desktop-i386, and it's 699MB, making me think that nothing is inherently wrong with the file I'm trying to burn. So I use InfraRecorder to burn it to an empty CD-R disk with 702MB of free space. (I tried using a DVD-R earlier, but switched over to CD-Rs after the DVD gave me the same problems that the CD-R is now giving me.) So I open up IR, find the ISO file, and burn it to the CD. Everything appears to work normally, and the disk pops out once it is done.

Now the Ubuntu website tells me that I can open up the CD-R file and check its contents, but I can't seem to do that, or at least on my computer. I put the disk back in (while running Vista on the computer I burned it on) and nothing happens, although I don't know if something is supposed to happen. I click on the DVD drive whilst in My Computer, and it pops out again (with the disk still in it) and tells me to insert a disk... whatever I think.

So maybe it's just not meant to work when already in Windows, but I put it into my Lenovo, boot from the CD/RW and am getting the same error. The specific error isn't really relevant, but rather the fact that it isn't even booting into Ubuntu. 

Clarifications:

The integrity of the ISO file or the distribution are not the cause. I downloaded Linux Mint and encountered the same problem.

The computer burning the disk is not the problem. I used InfraRecorder and other burning software on two different computers, and both got to 100% and ejected the disk. The problem is that the disk is full, but not doing anything on either of the two computers I'm using to burn, and isn't booting up on my Thinkpad.

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

1. Have you tried setting BIOS to boot from CD before the HDD?

2. This seems to be a problem for laptop users. The live CD just doesn't want to function correctly. I suggest that you copy the file named "wubi" and the .iso directly to your hard drive. 

Double click wubi to install Ubuntu. Don't bother with the cd at all. It's a fairly quick and painless install. It's also a quick and easy uninstall, if you decide not to continue using Ubuntu.

---

### Post by youradhere4222 on 2010-08-02
Well I need to boot from the CD directly, because the computer I'm trying to install it on doesn't have a functional OS at the moment. Is this still possible?

---

### Post by jroa on 2010-08-02
You may have a poorly burned disk.  Try burning again at the slowest possible speed.

Also, I had better luck when I used Vista to burn the CD instead of a stand alone program.  If you have Vista or Win7 on the computer that works, right click the iso and choose "Copy image to CD".  Vista and 7 will burn instead of copy.  Once again, do it on the slowest speed.

If this does not work, you might want to check the check sum on the iso to make sure it is correct.

---

### Post by Maverick_Meerkat on 2010-08-02
Ah... Well, that is a different situation. The standard live cd probably will not work for you. Try using the Alternate Text Only Install.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by jroa on 2010-08-02
Also, if you think the Windows is OK on the computer that won't boot and you just have a bad boot sector, you can use a program called GAG to boot the system.  It can be used live or installed permanently into the boot sector.  I would try to boot it live using a burned CD to see if either of your Windows partitions will boot.  If they do, then you just have to repair the boot records.

Edit:
Sorry, I did not read your reply before I posted.  I have used the live Ubuntu to load onto a system that had no operating system.  It should work fine if your CD is good.

---

### Post by Maverick_Meerkat on 2010-08-02
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by youradhere4222 on 2010-08-03
> **jroa said:**
> Also, if you think the Windows is OK on the computer that won't boot and you just have a bad boot sector, you can use a program called GAG to boot the system.  It can be used live or installed permanently into the boot sector.  I would try to boot it live using a burned CD to see if either of your Windows partitions will boot.  If they do, then you just have to repair the boot records.

Edit:
Sorry, I did not read your reply before I posted.  I have used the live Ubuntu to load onto a system that had no operating system.  It should work fine if your CD is good.
GAG worked perfectly - thank you so much! I can access my Windows partitions again, and I'm probably in a better position to install Ubuntu without a CD.

---

### Post by jroa on 2010-08-03
Glad I could help for a change, instead of being the one asking for help.  :)

---

### Post by Kyentei on 2010-08-03
What I was wondering though, you still can not boot Ubuntu, right? How about you try and boot Ubuntu from a USB stick? (created with unetbootin for instance)

---

### Post by jroa on 2010-08-03
Now that he can boot into Windows Wubi might work to install Ubuntu.  I have never used the Alternate Installation CD that Maverick_Meerkat mentioned, but that might work too.

---

