---
title: "Unable to install ubuntu 19.10"
date: 2019-12-10
forum: Installation &amp; Upgrades
---

### Post by alirezas on 2019-12-10
Motherboard: Asus Hero XI Maximus
CPU: Intel I9 9900K
GPU: Nvidia 2080 TI RTX
Harddrive: Sumasung m.2 nvme 1 tb
Ram: 32 gig 3200mhz

I am trying to install Ubuntu 19.10 from USB, and as it loads to usb the screen goes black with pixels and nothing happens and have to force restart everything.

I could not get anything installed and have no OS currently, any suggestions as what to do.

Thanks for your help in advance.

---

### Post by CatKiller on 2019-12-11
I've not tried to install 19.10, but my understanding is that the *package* for the proprietary driver is included in the live image, but the live image doesn't *use* the proprietary driver - since that would be broken on any system without Nvidia graphics.

That means that you're likely to still need to use nomodeset for the installation process, since the open source nouveau driver isn't as good at detecting the appropriate screen resolution.

---

### Post by The Cog on 2019-12-11
nomodeset is one of the Other options of the installer:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by alirezas on 2019-12-11
I can not even get to command line as the system loads usb, the screen goes black with pixels, I dont even get anything.

---

### Post by ubfan1 on 2019-12-11
If you get a grub menu display, the "Try Ubuntu without installing (safe graphics)" uses "nomodeset".  If you don't even get a grub menu, that menu item is the second one, so try a down arrow and Enter on your black screen.

---

### Post by oldfred on 2019-12-11
Many systems need UEFI updates & SSD firmware updates.
You will need nomodeset.

My now much older, Asus Z97 motherboard required several UEFI setting changed. And everytime I update UEFI, I have to redo settings. So I saved screen shots. 
[https://ubuntuforums.org/showthread.php?t=2296538](https://ubuntuforums.org/showthread.php?t=2296538)
         
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by alirezas on 2019-12-12
I did manage to install Ubuntu 19.10.  The issue I had was with Nvidia drivers.

Now the issue I got is, it takes 2 minutes to load to login screen and 2 minutes to shutdown, which I know is not normal.

---

### Post by ubfan1 on 2019-12-12
Try running dmesg in a terminal and see what is running when the 2 minute delay occurs.  Could be some wireless timeout, but could be a wrong UUID for a partition.

---

### Post by oldfred on 2019-12-12
My system says this, or 25 sec to totally boot, but from login to screen is less than 2 sec.
```
fred@bionic-z97:~$ systemd-analyze
Startup finished in 10.383s (firmware) + 4.121s (loader) + 2.674s (kernel) + 8.057s (userspace) = 25.237s
graphical.target reached after 1.565s in userspace


```

I have gone thru a lot of the threads & posts on slow boot.

These are the major things I have done.
       turned off NetworkManager-wait

  $ systemctl unmask NetworkManager-wait-online.service
 $ systemctl enable NetworkManager-wait-online.service 
 Changed systemctl daily timer 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps     

       [https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html) 
   [https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything)

---

### Post by rainbowraven on 2019-12-12
I’m also having this issue and your first link gives a 403 error for me, is it possible you could share those screenshots another way?

> **oldfred said:**
> Many systems need UEFI updates & SSD firmware updates.
You will need nomodeset.

My now much older, Asus Z97 motherboard required several UEFI setting changed. And everytime I update UEFI, I have to redo settings. So I saved screen shots. 
       [http://ubuntuforums.org/showthread.php?t=2296538Asus-ar%20screenshots%20oldfred](http://ubuntuforums.org/showthread.php?t=2296538Asus-ar%20screenshots%20oldfred) 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2019-12-12
Bad Fred.
I must have typed something right after the link in Zim & it made it part of link.
And I did not test it.
fixed it in post above.

---

### Post by alirezas on 2019-12-14
> **oldfred said:**
> My system says this, or 25 sec to totally boot, but from login to screen is less than 2 sec.
```
fred@bionic-z97:~$ systemd-analyze
Startup finished in 10.383s (firmware) + 4.121s (loader) + 2.674s (kernel) + 8.057s (userspace) = 25.237s
graphical.target reached after 1.565s in userspace


```

I have gone thru a lot of the threads & posts on slow boot.

These are the major things I have done.
       turned off NetworkManager-wait

  $ systemctl unmask NetworkManager-wait-online.service
 $ systemctl enable NetworkManager-wait-online.service 
 Changed systemctl daily timer 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps     

       [https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html) 
   [https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything)


Startup finished in 2.857s (kernel) + 1min 41.731s (userspace) = 1min 44.588s 
graphical.target reached after 1min 41.726s in userspace

---

### Post by alirezas on 2019-12-14
Also here is the critical chain:


systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 41.857s
&#9492;&#9472;multi-user.target @1min 41.857s
  &#9492;&#9472;kerneloops.service @7.554s +12ms
    &#9492;&#9472;network-online.target @7.551s
      &#9492;&#9472;NetworkManager-wait-online.service @1.170s +6.380s
        &#9492;&#9472;NetworkManager.service @1.051s +119ms
          &#9492;&#9472;dbus.service @1.049s
            &#9492;&#9472;basic.target @1.031s
              &#9492;&#9472;sockets.target @1.031s
                &#9492;&#9472;snapd.socket @1.028s +3ms
                  &#9492;&#9472;sysinit.target @1.027s
                    &#9492;&#9472;systemd-timesyncd.service @872ms +155ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @854ms +15ms
                        &#9492;&#9472;local-fs.target @853ms
                          &#9492;&#9472;run-user-124.mount @11.303s
                            &#9492;&#9472;swap.target @262ms
                              &#9492;&#9472;swapfile.swap @204ms +57ms
                                &#9492;&#9472;systemd-remount-fs.service @195ms +8ms
                                  &#9492;&#9472;systemd-journald.socket @191ms
                                    &#9492;&#9472;-.mount @189ms
lines 1-23

---

