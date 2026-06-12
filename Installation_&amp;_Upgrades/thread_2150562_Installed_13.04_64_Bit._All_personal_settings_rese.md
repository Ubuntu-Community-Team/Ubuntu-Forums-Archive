---
title: "Installed 13.04 64 Bit. All personal settings reset afer every reboot."
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by modalsurrealist on 2013-06-01
I have been using Ubuntu for a couple years, and in spite of knowing  little, i haven't really had any problems until i installed 13.04. It  all seemed to go smoothly, then installed all my favorite programs,  settings, background etc. Then i shut my computer down for the night and  when i came back to it, everything had been reset to the way i found it  after installing it. I then setup all my programs and settings all over  again, only to find the changes lost the next time i rebooted. This  happens every time. 

And on top of that, it will not let me create a new startup disk. 

When i try to erase my SD card in the Startup Disk Creator, i get this,

"org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible  causes include: the remote application did not send a reply, the message  bus security policy blocked the reply, the reply timeout expired, or  the network connection was broken."

I thought to try formatting the SD card with gparted, but when i click on gparted nothing happens.

I pulled out a brand new SD card i just bought, and that seemed to  "erase" just fine, so i click "Make Startup Disk", and get this,

"An uncaught exception was raised:
[Errno 13] Permission denied: '/tmp/tmp0dytve'."


Any ideas what wrong, or what i can do to get myself out of this mess?:mad:

---

### Post by 2F4U on 2013-06-01
Is it possible that you are running from a flash device instead of a hdd? That would explain why all settings and installed programs are lost after a reboot. While you can install programs and perform configurations on, for example, a usb flash drive, these are usually not persistent unless you create it with persistence option.

---

### Post by modalsurrealist on 2013-06-06
No. I have been booting from the SSD that i installed 13.04 . The problem has progressed. Now after logging on, not only do i not have any of my last changes, i do not have anything else. I just have the picture of my desktop, the icons on the left, nothing on the title bar at all, and i have no ability to do anything. I gave up a a few days, and finally found a way to boot this computer, using an old HHD i pulled out of the closet that still has 12.04 on it. Problem is, i have no idea what i was using for a password, so all i can do is use the Guest login, but still cannot make a startup disk. 

I don't really have a lot of time to try to figure this out, but i'm open to any ideas if you think there is still any hope. I think i'll probably have to use a friend's computer to make a new installation boot disk.

---

### Post by modalsurrealist on 2013-06-06
I borrowed a friend's laptop to make installation disks, and so far have installed 12.04 32bit, 12.04 64bit, and 13.04 32bit rewriting over the same drive, each time clearly having a new installation, but the situation after logging in is exactly the same. I can move my mouse around, but everything frozen, and the title bar at the top of the screen is empty. 

Could I have a virus? This is super bazaar!

---

### Post by oldfred on 2013-06-06
If you have newer computer with at least 2GB of RAM and a SSD, you should use the 64 bit version. If a SSD do you have AHCI on in BIOS?

If you can boot a liveCD or flash drive run the BootInfo report so we can see details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

### Post by modalsurrealist on 2013-06-06
Thanks for the replies. I'm working on it. First problem, "Try Ubuntu" is no better. Only difference is "start up disk creator" is on the sidebar, and the desktop back ground has the "Ubuntu" logo with the 5 dots. I'll have to try using one of these boot repair things.

---

