---
title: "Freezes on installation when connected to network"
date: 2019-01-01
forum: Installation &amp; Upgrades
---

### Post by erenbkts on 2019-01-01
Upper Note: The problem's cause is not network/network adaptor. Its reason is c-states. I explained the solution on the 2nd post. Mods please change the subject as I wrote on the second post.

Hello,

I am using a Dell Inspiron 15 7577 Gaming Notebook with i5-7300HQ CPU and Nvdia GTX 1050 4GB (not ti). It has 8 GB of RAM installed.

I (correctly) installed ubuntu-18.04.1-desktop-amd64 iso file on my 32 GB Sandisk Flash Drive. I shut down my computer (fully, without fast start-up). Plugged the USB Drive and started it, clicked on F12 and selected the usb drive. GRUB menu showed up, I selected install Ubuntu. did everything well but when it comes to selecting and connecting to a wireless network, I selected it, wrote the password and clicked on connect. And BUM. Notebook turned into a brick. Even my capslock led was not answering when I push on it. Screen on, but not moving a single thing. It is just like a brick.

I shut down the notebook by hold-pressing the power button. I again started with usb but now I selected "Try ubuntu before installing". it was working like a charm *_TILL I CONNECT._* 

I am ready to show you every report as you tell me how to do, I am ready to do every solution you give me. I need that ubuntu on my notebook.

My network connection is not making a trouble like this on Windows 10. Also, I want to dual boot these systems. 

I will be glad if some answer fix my problem. Thanks for reading. I am now watching this thread to be answered by keep pressing f5 every second.

---

### Post by erenbkts on 2019-01-01
The problem was not being caused by network etc.

The C-states was making a problem (I think after a while cpu disconnects the USB disk for 

Solution:

1.  I plugged the usb disk on notebook while Windows was on, and in usb disk I opened /boot/grub directory on file explorer.

2.  I edited the both grub.cfg and loopback.cfg files with notepad by changing the "try ubuntu without installation" parts lke this:

(you can copy this and paste there)
> menuentry "Try Ubuntu without installing" {    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash intel_idle.max_cstate=1 ---
    initrd    /casper/initrd.lz

!.  Dont forget. Change these lines on both grub.cfg and loopback.cfg files.

4.  Shut down windows (be sure fastboot is disabled)

5.  Start PC with USB plugged. select usb . select Try ubuntu w/o installation (first entry on grub menu)

6.  The else is the same with a normal installation.

7.  After installation, do everything that Zanna says on this page: [https://askubuntu.com/questions/794083/ubuntu-16-04-freezes-after-15-to-20-seconds-of-use](https://askubuntu.com/questions/794083/ubuntu-16-04-freezes-after-15-to-20-seconds-of-use)



Mods please change the subject as "Installation freezes after a while on Dell Inspiron 15 7577". Thanks

---

