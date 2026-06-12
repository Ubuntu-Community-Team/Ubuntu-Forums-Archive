---
title: "2 hard drives, one for Ubuntu, one for XP"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by Gary100 on 2011-09-22
My computer is a dual boot, Ubuntu 10.04 and Windows XP Pro. It’s a Dell 4600, and F12 brings up the boot menu.
   
  I inherited a new hard drive, so I thought I’d install Ubuntu on the new hard drive, with the idea that when I wanted Ubuntu, I’d restart the computer, hit F12, choose the new drive, and be logged into my New Drive and Ubuntu. The idea is to eventually uninstall Ubuntu from XP’s Drive, and have the New Drive hosting only Ubuntu. No more pesky games with partitioning and sharing.
   
  From 10.04, I made a bootable USB drive as per [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). I rebooted my computer, hit F12, and I got Ubuntu. I followed instructions on that web site to install 10.04 on my new hard drive.
   
  Later, after removing the bootable USB Drive, I restarted the Dell again, hit F12 and tried to boot from the new drive. Nothing happened, I could not boot this way. I restarted again and did not hit F12. The dual boot choices came up as always, with an addition choice I did not see before. I took it, and sure enough, it was the new Ubuntu on the new disk,  I knew this was so from the tiny amount of space ( ~2.6 Gig) this new installation took up.
   
  [FONT=&quot]What’s wrong in my thinking? Why was I able to boot the USB drive via F12 and not the hard drive that way? I was hoping to get new Ubuntu working before I uninstall old Ubuntu, if that’s possible, because I prefer to do one thing at a time, if possible.[/FONT]

---

### Post by oldfred on 2011-09-22
If you used the automatic install, it wrote the grub2 boot loader to sda. But some computers make the USB sda or an IDE drive sda, so we cannot always be sure where grub goes. Always best to use manual install when you have more than one drive, so you can choose where grub goes.

To see where your grub boot loader is:


Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

