---
title: "Not booting - Stuck on splash screen"
date: 2023-08-07
forum: Installation &amp; Upgrades
---

### Post by philrego on 2023-08-07
Computer ran out of battery and shut off. Might have been in sleep mode. Before this it was working with no issues. No recent changes. Laptop always gets stuck on the splash screen, Dell logo with smaller Ubuntu logo under it. I ran boot-repair it said it was sucesful but it didnt help. I ran fsck and grub. Tried booting with older version on recovery screen.

boot-repair logs
[https://paste.ubuntu.com/p/CJ4XFFvb3w/](https://paste.ubuntu.com/p/CJ4XFFvb3w/)

---

### Post by oldfred on 2023-08-07
If you get the screen with both vendor logo & ubuntu, you are past grub boot issues and into something else. Most often video, but could be anything.

Can you boot to grub menu?
If only one install in UEFI mode, you have to press escape just after vendor logo & before grub menu normally appears.
And then boot recovery mode?
Recovery mode has menu with several options for fixes.

---

### Post by philrego on 2023-08-07
Yes I can get to the Grub CLI and boot recovery mode, but I don't know what to do when I get there.

In boot recovery mode I've already tried running [COLOR=#000000]fsck[/COLOR]

---

### Post by oldfred on 2023-08-07
What model Dell & what video card/chip?

If you turn networking on, can you update system?
sudo apt update
sudo apt upgrade

---

### Post by philrego on 2023-08-07
Dell Latitude 7420. Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] rev 01

I was able to update/upgrade after editing resolv.conf. I installed rEFInder and ran boot-repair again, but I still can't get past the splash screen. 

I followed this guide but just got stuck on reboot with these logs on the screen:
[https://www.howtogeek.com/887757/how-to-use-grub-rescue-to-fix-linux/](https://www.howtogeek.com/887757/how-to-use-grub-rescue-to-fix-linux/)
> [FONT=Arial] [ OK ] Finished GRUB failed boot detection.[/FONT][FONT=Arial]1[/FONT]
[FONT=Arial]AAn[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]Started IIO Sensor Proxy service.[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]Started Network Manager[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]][/FONT]
[FONT=Arial]Started Power Profiles daemon.[/FONT]
[FONT=Arial][ OK ] Finished Remove Stale online ext4 Metadata Check Snapshots.[/FONT]
[FONT=Arial][ OK ] Started Switcheroo Control Proxy service.[/FONT]
[FONT=Arial][ OK ] Started Bluetooth service.[/FONT]
[FONT=Arial][ OK ] Started User Login Management.[/FONT]
[FONT=Arial][ K ] Reached target Bluetooth support.[/FONT]
[FONT=Arial]Start ing Modem Manager..[/FONT]
[FONT=Arial]Starting Netuork Manager Wait Online...[/FONT]
[FONT=Arial]Start ing Thunderbolt system service..[/FONT]
[FONT=Arial]Starting Load/save Screen Backlight Brightness of leds:de1l::kbd_backlight.[/FONT]
[FONT=Arial]Start ing Hostname Service...[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]Started Disk Manager[/FONT]
[FONT=Arial]L L[/FONT]
[FONT=Arial]Found device Ni-FI 6 AX201.[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]started Accounts service.[/FONT]
[FONT=Arial][ OK ] Started Dispatcher daemon for systemd-netuorkd.[/FONT]
[FONT=Arial]Start ing changes mac for wlpos2of3.[/FONT]
[FONT=Arial][FAILED] Failed to start changes mac for ulpos2of3.[/FONT]
[FONT=Arial]see 'systemctl status changemacoulposzof3.service' for details.[/FONT]
[FONT=Arial]OK ] Reached target Network[/FONT]
[FONT=Arial][[/FONT]
[FONT=Arial]Start ing CUPS scheduler.[/FONT]
[FONT=Arial]starting dnsmasa - A lightweight DHCP and caching DNS server...[/FONT]
[FONT=Arial]Start ing OpenVPN service.[/FONT]
[FONT=Arial]Start ing Permit User Sessions.[/FONT]
[FONT=Arial]OK OK OK D OK[/FONT]
[FONT=Arial]] Started Unattended Upgrades Shutdoun.[/FONT]
[FONT=Arial]AAAA[/FONT]
[FONT=Arial]] Finished Process error reports uhen automatic reporting is enabled.[/FONT]
[FONT=Arial]Finished OpenVPN service.[/FONT]
[FONT=Arial]Finished Permit User Sessions.[/FONT]
[FONT=Arial]][/FONT]
[FONT=Arial]Started Thunderbolt system service.[/FONT]
[FONT=Arial]Starting GNOME Display Manager..[/FONT]
[FONT=Arial]Starting Hold until boot process finishes up...[/FONT]
[FONT=Arial]RR OK OK OK[/FONT]
[FONT=Arial]Started CUPS Scheduler.[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]Started LSB: This services starts and stops the USB Arbitrator..[/FONT]
[FONT=Arial][ OK ] Finished Hold until boot process finishes up.[/FONT]
[FONT=Arial]Starting Set console scheme.[/FONT]
[FONT=Arial]J Finished Set console scheme.[/FONT]
[FONT=Arial]Started Modem Manager[/FONT]
[FONT=Arial]Created slice Slice /system/getty.[/FONT]
[FONT=Arial]Started GNOME Display Manager[/FONT]
[FONT=Arial][FAILED] Failed to start dnsmasg - A lightueight DHCP and caching DNS server.[/FONT]
[FONT=Arial]See 'systemct1 status dnsmasq.service' for details.[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]Started Hostname Service.[/FONT]
[FONT=Arial]Reached target Host and Network Name Lookups.[/FONT]
[FONT=Arial]OK[/FONT]
[FONT=Arial]Starting Netuork Manager Script Dispatcher Service...[/FONT]
[FONT=Arial]OK 1 Started Metwork Manager Script Dispatcher service.[/FONT]
[FONT=Arial]OK 1 Finished Netuork Manager Hait Online.[/FONT]
[FONT=Arial]RRRR OK OK[/FONT]
[FONT=Arial]1 Reached target Metwork is Online.[/FONT]
[FONT=Arial]1 Started Dounload date for packeges that falled at package install time.[/FONT]
[FONT=Arial]1 Started Check to see uhether there is a new version of Ubuntu available.[/FONT]
[FONT=Arial]Reached target Timer Un!ts,[/FONT]
[FONT=Arial]Started ClamAy virus database updater,[/FONT]
[FONT=Arial][ OK 1 Started Make remote CUPS printers available locally.[/FONT]
[FONT=Arial]Start ing Too1 to automat ically collect and submit kernel crash signatures...[/FONT]
[FONT=Arial]1 Started crash report submission.[/FONT]
[FONT=Arial]RRR[/FONT]
[FONT=Arial]] Started Tool to automat ically collect and submit kernel crash signatures.[/FONT]
[FONT=Arial]R 1 Created slice User S14ce of UID 1000,[/FONT]
[FONT=Arial]Start ing User Runtime Directory /run/user/1000...[/FONT]
[FONT=Arial][ OK Ok[/FONT]
[FONT=Arial]Finished User Runt ime Directory /run/user/1000.[/FONT]
[FONT=Arial]Start ing User Manager for UID 1000,[/FONT]
[FONT=Arial][ OK OK ! F inished Load/save Screen Backlight Brightness of leds:dell::kbd_backlight.[/FONT]
[FONT=Arial][ OK ] Started User Manager for UID 1000.[/FONT]
[FONT=Arial]OK OK[/FONT]
[FONT=Arial]started Session 1 of User ph41.[/FONT]
[FONT=Arial]1[/FONT]
[FONT=Arial]Start ing Realt imekit Scheduling Policy Service,,.[/FONT]
[FONT=Arial][ OK OK 1 Started Realtimekit Scheduling Policy Service.[/FONT]

---

### Post by oldfred on 2023-08-07
It showed this, but continued to boot.
[FONT=Arial]Start ing changes mac for wlpos2of3.[/FONT]
[FONT=Arial][FAILED] Failed to start changes mac for ulpos2of3.[/FONT]
[FONT=Arial]see 'systemctl status changemacoulposzof3.service' for details.

No idea what that is.

I have a Dell 5310 with 11th Gen Intel. 
Using Kubuntu 22.04 and originally had 5.15 kernel. Just yesterday updated it to 6.2 kernel with no issues.
[/FONT]

Do you have latest UEFI firmware from Dell?
Linux now has updates for recent Dell systems.
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update

---

### Post by philrego on 2023-08-08
I ran these commands. It updated the BIOS. Ran the commands again and it says no more updates. But still cant get past the splash screen.

---

### Post by oldfred on 2023-08-08
Boot to terminal with recovery mode.
Run this, but many lines are not important. Just warnings or a command with "error" in the command.
sudo grep -E -i "error|warning" /var/log/dmesg

---

### Post by philrego on 2023-08-08
Press Enter for maintenance
(or press Control-D to continue):
rootophil-Latitude-7420:"# sudo grep -E -i "error|warning" /var/log/dmesg

0.000000] kernel: x86/split lock detection: #AC: crashing the kernel on kernel split_locks and warning on user-space split_locks

0.612926] kernel: 18042: Harning: Keylock active

0.815379] kernel: RAS: Correctable Errors collector initialized

4.070072] kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_T2.ETMD], AE_NOT_FOUND (20221020/psargs-330)

4.070107) kernel: ACPI Error: Aborting method \_SB.IETM._OSC due to previous error (AE_NOT_FOUND) (20221020/psparse-529)

https://i.ibb.co/sJ01r6f/20230809-075730.jpg

---

### Post by oldfred on 2023-08-08
AE_NOT_FOUND has been posted multiple times and most say it does not matter.

ACPI errors typically do not matter.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1870995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1870995)
Do you have a keyboard plugged in via a docking station?
And have you updated firmware on docking station. Not sure if fwupdate would have updated that.

Or not really seeing much in the way of real errors.

---

### Post by philrego on 2023-08-09
Nothing is conneted to the laptop but the charger. I don't have a docking station. 

It boots to Ubuntu installation flash drive just fine. Why can't it just reinstall the boot loader instead of the whole computer? I don't want to reinstall Ubuntu.

---

### Post by oldfred on 2023-08-09
If you get grub menu, reinstalling grub will not solve issue.
And if you can boot recovery mode, it should let you update.
It is something else.

When I look up Dell 7420, it says 11th gen Intel.
But Tigerlake is 12th Gen
Did they do an update?

What live installer version are you using?

---

### Post by tea for one on 2023-08-09
```
Ubuntu, with Linux 6.2.0-26-generic   a0de46c8-6e1b-435d-83e2-65bb8104f24b
Ubuntu, with Linux 5.19.0-50-generic   a0de46c8-6e1b-435d-83e2-65bb8104f24b
```
Have you tried to boot using kernel 5.19.0-50?

---

### Post by philrego on 2023-08-09
I think I already updated everything. Not sure what CPU it is.

---

### Post by philrego on 2023-08-10
Tried that but still stuck on splash screen

---

### Post by MAFoElffen on 2023-08-10
Do you get to a Grub2 boot menu?

If yes, at the Grub2 Boot menu, press the <E> key. <Arrow-Down> to the line that starts with 'linux"... <Arrow-Right to the beginning of the words "quiet splash". Replace the word "quiet splash" with "--- 3 split_lock_detect=off". Press <Cntrl><X> to boot...

Does it boot to a Console Login prompt? If so, enter your username and password...

Copy down and post the output of 
```

sudo lshw -c video -businfo

```
If it doesn't do one of the steps, stop and tell us...

---

### Post by philrego on 2023-08-10
> **MAFoElffen said:**
> Do you get to a Grub2 boot menu?

If yes, at the Grub2 Boot menu, press the <E> key. <Arrow-Down> to the line that starts with 'linux"... <Arrow-Right to the beginning of the words "quiet splash". Replace the word "quiet splash" with "--- 3 split_lock_detect=off". Press <Cntrl><X> to boot...

Does it boot to a Console Login prompt? If so, enter your username and password...

Copy down and post the output of 
```

sudo lshw -c video -businfo

```
If it doesn't do one of the steps, stop and tell us...

[https://gcdnb.pbrd.co/images/RFPXQFMV9C7E.jpg?o=1](https://gcdnb.pbrd.co/images/RFPXQFMV9C7E.jpg?o=1)

---

### Post by MAFoElffen on 2023-08-10
So it boots the kernel to console and allows you to log in. So it is the grapgics layer that is not coming up. 

For graphics, it has 11th Gen iCore with Tiger Lake-LP GT2 Iris Xe Graphics,where Intel was changing things...

These are my notes for installing Intel XE Graphics drivers for 11th Gen and newer. You might want to print these instructions out so you can type the commands into the console of that machine.
```

uname -r 
# Confirm that the kernel is 5.19.0 or newer for 11th Gen iCore... 
# If not, install kernel to meet requirements.

sudo apt update
sudo apt install --reinstall -y gpg-agent wget
wget -qO - https://repositories.intel.com/gpu/intel-graphics.key | \
  sudo gpg --dearmor --output /usr/share/keyrings/intel-graphics.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/intel-graphics.gpg] \
  https://repositories.intel.com/gpu/ubuntu jammy/production/2328 unified" | \
  sudo tee /etc/apt/sources.list.d/intel-gpu-jammy.list
sudo apt update
sudo apt install -y intel-i915-dkms xpu-smi
sudo reboot -P now
sudo apt-get install -y \
  intel-opencl-icd intel-level-zero-gpu level-zero \
  intel-media-va-driver-non-free libmfx1 libmfxgen1 libvpl2 \
  libegl-mesa0 libegl1-mesa libegl1-mesa-dev libgbm1 \
  libgl1-mesa-dev libgl1-mesa-dri libglapi-mesa \
  libgles2-mesa-dev libglx-mesa0 libigdgmm12 libxatracker2 \
  mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers \
  va-driver-all vainfo hwinfo clinfo


stat -c "%G" /dev/dri/render*
groups ${USER}

# Check to see if User is member of render group. 
# If not do:
newgrp render
sudo gpasswd -a ${USER} render

```

---

### Post by philrego on 2023-08-10
How do I login to my ubuntun drive when I'm running the Live USB? There's no internet in the GRUB menu. I have live USB running now. I want to log into the SSD drive. I had the command for it before but lost it

No internet without gui https://gcdnb.pbrd.co/images/zR4D3j8DXi5d.jpg?o=1

---

### Post by oldfred on 2023-08-10
If you boot to grub menu and boot recovery mode of any of the kernels listed, you can turn on Internet there and can open terminal to run commands.

---

### Post by MAFoElffen on 2023-08-10
Wait...

oldfred asked you to go to the recovery menu from the Grub2 of the installed system, without using the LiveUSB media:
In the recovery menu... Selecting "network" with enable networking, then mount the filesystem as read/write. Then it will return to the menu. Then select "root', which will drop to a root prompt, saying press enter to go to maintenance mode...

If you did what I added instructions for... Did you do that from the Grub2 of the installed system or from LiveUSB? I assumed you would follow those directions, without using the LiveUSB. It that mode, you would have booted to your installed system, in init mode 3, which would be on the installed system, with it's networking. Did you not do that?

---

### Post by philrego on 2023-08-11
I had to "nmcli radio wifi on" for the internet to work in recovery mode. Even after selecting "enable networking" and "drop to shell" 

Also able to connect to the drive from Live USB using [https://askubuntu.com/a/1481970/623503](https://askubuntu.com/a/1481970/623503)


I reran these commands from recovery mode 
sudo fwupdmgr get-devices 
sudo fwupdmgr get-updates 
sudo fwupdmgr update

I ran all the commands you gave from recovery mode and while connected to my drive on Live USB. Got one error. Still can't past splash screen.

https://photos.app.goo.gl/pbJiRWU5KWGNVrEE6

---

### Post by oldfred on 2023-08-11
While your askubuntu link is for chroot, it did not include the mount of the ESP as shown in the link provided by oldfred's comment.

---

### Post by philrego on 2023-08-11
I reran everything from LiveUSB with EFI and main drive mounted. It wasn't able to install [COLOR=#000000][FONT=&quot]intel-i915-dkms.

I disabled auto-sign in. It boots to the sign in screen now, but freezed when I log in. The first time I tried to login I selected Wayland and I was able to login (I had Wayland permenatly disabled before), but after restart I haven't been able to login again, it just freezes. 

The kernal version got downgraded to 5.15.0-78 somehow and that's the only option I see to boot now. [/FONT][/COLOR]

---

### Post by philrego on 2023-08-13
After reformatting my entire computer, restoring my backups, and running apt update/upgrade, I still have the same issue. I don't know what apt package is causing this.

---

### Post by philrego on 2023-08-14
I reinstalled Ubuntu again. I ran "Software Updater" and it's still working fine. I havn't restored my backup or ran apt upgrade. Not sure if my issue is with an apt package or my backup. Not going to update anything unless I need to.

---

### Post by oldfred on 2023-08-14
What is included in your backup?

I typically just backup my data which not all of is in /home, /home and only a few files in /etc that I have manually edited (grub). I export a list of installed apps to make it easy to reinstall all the ones I normally add. I do not have any server apps like web or database, so do not have to back those up.

If your backup is entire system, then you probably are restoring a misconfigured file.

---

### Post by philrego on 2023-08-15
Found the issue it was this line in my .bashrc that was suppose to disable wakeup on mouse movement. 
> sudo sh -c "echo 'disabled' > /sys/bus/usb/devices/3-3/power/wakeup"
When I add this line the computer gets stuck on the splash screen.

---

