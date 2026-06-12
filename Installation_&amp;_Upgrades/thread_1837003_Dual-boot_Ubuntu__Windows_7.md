---
title: "Dual-boot Ubuntu / Windows 7"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by paihungchen on 2011-09-01
Hi,
 
I am totally new to Ubuntu (and to Unix/Linux in the broader sense). I just tried to install Ubuntu on a Windows 7 Toshiba laptop by running Ubuntu's Windows installer as indicated here:
 
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
 
The installation succeeded. After I rebooted the laptop, I saw two boot options as expected: Windows 7 and Ubuntu, and I selected Ubuntu. However, after "booting" into Ubuntu, all I saw is a black full-screen command-line shell with "GRUB" as the prompt. I tried some simple commands and the only one that worked is "ls" (not even "cd", "mkdir", etc.). I suppose this shouldn't be what it is supposed to be? May it be because my laptop only has one partition (C: drive) in it?
 
I guess it should be plenty obvious that I am a total newbie here. Any help is much appreciated!
 
Thanks,
Pai-Hung

---

### Post by Mark Phelps on 2011-09-01
Some folks will probably tell you to simply reinstall -- but anything you do at this point is going to risk damaging the Win7 setup, so BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.

That will allow you to restore Win7 boot if an Ubuntu reinstall or repair somehow corrupts it.

---

### Post by Reg71 on 2011-09-01
I just bought a toshiba nb505 about a week or so ago and I have it dual booting so if there is something I can look at in my config files that would help, I 'd be glad to.  I'm pretty new to ubuntu also but I use it for most everything I do on my computer and only boot over to windoze if I am gonna watch netflix or use my citrix client.  I used the setup procedure listed on ubuntu.com download page for the USB stick installation from windows.  I dont reacall any trouble with it, but I've slept since installing so I probably forgot everything.  Good luck in getting going.

---

### Post by jahboi on 2011-09-01
> **Reg71 said:**
> I just bought a toshiba nb505 about a week or so ago and I have it dual booting so if there is something I can look at in my config files that would help, I 'd be glad to.  I'm pretty new to ubuntu also but I use it for most everything I do on my computer and only boot over to windoze if I am gonna watch netflix or use my citrix client.  I used the setup procedure listed on ubuntu.com download page for the USB stick installation from windows.  I dont reacall any trouble with it, but I've slept since installing so I probably forgot everything.  Good luck in getting going.

DID you partition your system from the windows side(shrik volume etc). I intend installing ubuntu via the usb stick method. appears its works fine. *** linux newBie**

---

### Post by rreyes3713 on 2011-09-01
Did you install Ubuntu in the Window 7 environment as though it was an app (Wubi installation)?

Or did you install it where it boot of the CD or USB flash drive?

Want to clarify your installation before troubleshooting your problem.

---

### Post by paihungchen on 2011-09-02
I installed via Wubi. I just realized that Ubuntu requires a dedicated disk partition to install. I understand there are tools that can resize an existing NTFS partition to make room for a new partition. So I think the "get it to install correctly" part is taken care of.
 
May it still be considered a surprise that Wubi successfully added a Ubuntu booting entry in my boot menu and my Windows 7 still boots/works fine, given that my laptop only has one partition? :)
 
Pai-Hung

---

### Post by jahboi on 2011-09-02
> **paihungchen said:**
> I installed via Wubi. I just realized that Ubuntu requires a dedicated disk partition to install. I understand there are tools that can resize an existing NTFS partition to make room for a new partition. So I think the "get it to install correctly" part is taken care of.
 
May it still be considered a surprise that Wubi successfully added a Ubuntu booting entry in my boot menu and my Windows 7 still boots/works fine, given that my laptop only has one partition? :)
 
Pai-Hung

Hi, So you mean your win 7 pc has no partition for recovery ?
Just want to confirm some details, because i intend installing on a PC (most probably with a small partition for recovery)

---

### Post by Reg71 on 2011-09-02
> **jahboi said:**
> DID you partition your system from the windows side(shrik volume etc). I intend installing ubuntu via the usb stick method. appears its works fine. *** linux newBie**

I booted the USB stick and went from there.  It worked like a champ for me.  Wish I could be more help to the OP but I haven't run into any major probs with natty other than I didn't like unity so I switched to classic.  I'm on a netbook, and I still like the classic look better.

---

### Post by paihungchen on 2011-09-02
> **jahboi said:**
> Hi, So you mean your win 7 pc has no partition for recovery ?
Just want to confirm some details, because i intend installing on a PC (most probably with a small partition for recovery)
 
Actually there is indeed a 100MB system recovery partition on my Windows 7. In this case, what's Wubi's installation behavior?
 
From my experience this setup doesn't seem to work (and hece my asking on this thread), but fortunately my Windows 7 still works fine.

---

### Post by paihungchen on 2011-09-02
> **Reg71 said:**
> I booted the USB stick and went from there. It worked like a champ for me. Wish I could be more help to the OP but I haven't run into any major probs with natty other than I didn't like unity so I switched to classic. I'm on a netbook, and I still like the classic look better.
 
Does **booting into USB/CD and then installing from there** work for the common scenario of a manufacturer-pre-configured Windows laptop with a large user partition and a small recovery partition (no room left for a 3rd partition)?

---

### Post by jahboi on 2011-09-02
> **Reg71 said:**
> I booted the USB stick and went from there.  It worked like a champ for me.  Wish I could be more help to the OP but I haven't run into any major probs with natty other than I didn't like unity so I switched to classic.  I'm on a netbook, and I still like the classic look better.

is your windows OS a 32 or 64 bit ?

---

### Post by rreyes3713 on 2011-09-02
Since its Wubi installation, can you go into your Window 7 and un-install Ubuntu?

Try that just to recover your Window 7.

Then I would install Ubuntu using CD or USB flash drive. I assume you got to part where your computer boots off the CD or Flash Drive giving you a menu whether to install or pre-Drive [?] Ubuntu.

If you select installation:

During installation you will have step asking you if you want to manual partition the hard drive select "Yes" and you will have a bar graph with slide button. Sliding it to your left will decrease Window Partition, increasing Ubuntu partition. (This is 10.04). 

Ask more questions if I confuse you. 

I've done this installation a half of dozen times, blowing all of them except the last (lol) But if I have to do this again, I think I could do this installation without any hang ups.

---

