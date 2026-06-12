---
title: "Triple boot Windows 8, Ubuntu 12.10 and Backtrack (Ubuntu 10.04) problem"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by jonathanfv on 2013-01-06
Hi people. I'm more or less a Linux newbie, and I'd need some assistance here. Something is wrong with my Grub installation, and I have a hard time fixing it.

Booting Windows 8 and Ubuntu 12.10 works fine, but I can't get Backtrack to start when I select it in Grub. All I get is an empty screen, and nothing happens. Ever. However I'm really happy with my Ubuntu configuration. I installed Gnome 3 (after all, I don't even like it better than Unity) and KDE (it's the one I chose to use after trying Unity and Gnome, it's easy to configure docks of my choice and to customize the buttons, although I wish I had even more options), and succeeded to get my graphics card to work (Quadro K1000M) with Bumblebee.

I'm using a Thinkpad W530 (I received it 2 days ago, it's awesome!), so it uses UEFI, but I set the bios to "legacy mode" and deactivated the "safe boot" option to be able to boot Backtrack.

Here's what my partitions look like:

sda1: ntfs,  1000 MB
sda2: fat32,  250 MB
sda3: unknown, 128 MB
sda4: ntfs (Windows), 47.6 GB
sda5: linux-swap, 5 GB
sda6: fat32(cross compatible sharing space), 20 GB
sda7: ext4 (Ubuntu 12.10), 100 GB
sda8: ext4 (Ubuntu 10.04), 30 GB
sda9: ext4 (Data drive), 494.68 GB

And here's how I did my installation:
1. Installed Windows 8 using the recovery disk
2. Used Windows 8 to reduce the size of the Windows partition
3. Used Backtrack to format the partitions like I wanted them
4. Installed Backtrack on sda8 without a bootloader
5. Installed Ubuntu 12.10 on sda7 with Grub on sda
6. Spent a lot of time arranging Ubuntu to my liking, it's going to be my main OS

Once I was done configuring Ubuntu,  I wanted to reboot to Backtrack to configure it, but it wouldn't work. So using Ubuntu, I tried boot-repair. Didn't work. So I installed grub-customizer to look at my grub installation. The menu for Ubuntu 10.04 was in OS prober mode, so I changed it to a direct Linux boot on sda 8. Didn't work. So I installed a bootloader in sda8 directly. Didn't work. I changed again the first stage bootloader's Ubuntu 10.04's menu to chain loader. Didn't work either.

So, can anybody please tell me how I'm supposed to get it to boot? Is it a problem because the UEFI isn't supported by Backtrack (which is essentially Ubuntu 10.04)?

Thank you. Otherwise, I enjoy Ubuntu very much, it's a good OS, much better than Windows 8 (I tried liking it <snip>), and infinitely more free than OS X (which I had in a dual boot with Backtrack on my Macbook, which is now dying).

---

### Post by Old_Grey_Wolf on 2013-01-06
It is possible that you need to install the graphics drivers in BackTrack. 

Reboot and keep your finger on the Shift key untill you get the grub menu. Highlight the Backtrack entry and replace &#8220;quiet splash&#8221; with &#8220;nomodeset&#8221;.  Use Ctrl+x to continue booting. Once logged in install the graphics drivers.

---

### Post by jonathanfv on 2013-01-06
Thanks for the suggestion. I tried to do that just now, but it didn't change anything (the shift button didn't work, so I edited to boot command to add "nomodeset" after the linux parameters). I'm really wondering how come it does that. I think I should try to install Backtrack by itself on a different drive, to see if I can boot it just by itself.

---

### Post by jonathanfv on 2013-01-14
Just a little up, I haven't had the chance to try with a different drive yet cause I need to buy a new USB key (I don't have any free hard drive at the moment), my actual key being held in hostage by the Windows backup. Sorry for the time it takes, if anybody has the same problem.

---

### Post by darkod on 2013-01-14
I think you are actually using UEFI boot without knowing it. And that might be your issue. You say you set bios to legacy boot, but in your partitions list I don't see an extended partition. You list all partitions as "primary", which is possible only on gpt table. And windows doesn't work on gpt without uefi.

So, in your place I would confirm the table type because the windows install might have done it with gpt without telling you anything about it. That's the windows way, it always thinks it knows more than you.

Check the partition type with parted, it will tell you the type:
sudo parted -l (that's small L)

If it's gpt, I still haven't seen a case of windows working on gpt without uefi, so I think you might have a hybrid legacy/uefi system.

---

### Post by jonathanfv on 2013-01-14
Thanks a lot for the answer. You're right, I do have a GPT partition table, not an MSDOS one. I haven't rebooted to check the Bios again, but I'm pretty sure it's in hybrid mode right now as well.

I guess I'll just wait to get a good, fast USB 3.0 key, and then install BT on it instead.

---

