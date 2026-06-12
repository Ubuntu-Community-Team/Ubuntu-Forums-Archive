---
title: "Reply where to install grub2"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2010-06-07
I am getting ready to fresh install 10.04  But I have seen several post that when it comes to the part of installing grub2 people are responding incorrectly where to install grub2 and overlaying the vista mbr. They are left unable to boot windows and it looks quite involved to recover. Where can I find the text I can expect to see and how should I reply? 
I am currently running 9.04 dual boot with vista and grub legacy. I have four partitions. Vista, hp recovery, Ubuntu 9.04 and swap.  I plan to defrag vista and make my ubuntu partition bigger and then do fresh install but I am worried about wiping out my windows.  So where can I find documentation of what I can expect to see asked and how do I reply. Thanks

---

### Post by ronparent on 2010-06-07
I had this handy having just replied to another post.

[http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html)

---

### Post by oldefoxx on 2010-06-07
There are several factors involved, the primary one being which drive and partition represents C: to Windows.  You might think it would always be the first drive first partition, but that is where other factors kick in, such as a mix of SATA, IDE, and even USB drives on that PC.  In this regard, any smart card ports and such show up as additional drives, and since the BIOS, Windows, and Windows installer each have their own rules about which is the first drive, it is easy to make mistakes.

One way to try and get around this is to physically disconnect any unnecessary drive for starters.  Trouble is, when the other drives are reconnected, the order can change again under some slightly different circumstances.  Another way is just to repeat steps and try to make certain effects apply to more than one drive.  For instance, if offered a chance to put grub on (hd0), you can do  that one time, then then next time make it (hd1), and even (hd2) if dealing with three hard drives.  Or you could specify (fd0) and put the boot the whole grub process on the floppy drive.  You may not think you have this option, but on the Ubuntu LiveCD, it generally shows up under an Advanced button link.

Grub will include a link to booting to any installed Windows OS instead.  If your preference is to keep the Windows way of booting up, you can put grub elsewhere and use a tool like backpart to create a link to it that you can add to boot.ini.  I should add that in place of a hard drive or floppy drive to do the boot up, you can use a CD or DVD, or even a USB device.  If you aren't sure how, just do a search online with the info that
you relate to get down to the way you want to do it.

---

### Post by oldfred on 2010-06-07
The issue is not with new installs unless you choose to make the mistake but with upgrades from either 8.04 or 9.10. In windows everything is called a drive - c , d etc. But those drives in windows are really partitions. Drives refer to physical hard drives and are sda, sdb etc. The instructions on upgrade say to install grub to all drive, but then present a checklist of every drive & partition, so many are checking them all.

If you have only one drive you install grub to sda and it will default to that. You should look at the advanced button to see that it installs grub to sda, but do not install to sda1 or any  partition windows is in.

Instructions and even the screens do not vary significanly between versions.

The advanced button:
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)
Dual Boot win/10.04
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by Benchrest on 2010-06-13
Well I have 10.04 installed with updates.  Still a lot of work to do.  But I walked away while the install was in process from the install disk and when I came back it was done and ready to reboot.  Never asked a question about grub2. But when I rebooted it was there, vista and Ubuntu 10.04 both boot fine. Need to do a bit of tailoring but a ok. Resolved. Was not an issue.

---

