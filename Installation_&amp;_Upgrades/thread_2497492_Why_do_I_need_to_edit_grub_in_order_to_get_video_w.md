---
title: "Why do I need to edit grub in order to get video with 24.04?"
date: 2024-05-07
forum: Installation &amp; Upgrades
---

### Post by Keith_Helms on 2024-05-07
I have a fairly new Asus Tuf A16 laptop and when I installed either Xubuntu 24.04 or Ubuntu Cinnamon 24.04 on it, it will restart normally ONCE when the install finishes, but the 2nd time around I just get a blank screen.  There don't seem to be any obvious error messages in the syslog.  I found some postings talking about editing /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quite splash"
```
and removing the "quiet splash" text and for some reason that solved the problem.

What does that grub line have to do with whether I get video on 24.04?

EDIT:

If I boot in recovery mode I do get a nice VGA resolution desktop, but when I select "resume boot" the no-video problem comes back.

---

### Post by MAFoElffen on 2024-05-07
I'm not sure, meaning "not positive".

Usually that would be required if you had NVidia, but sometimes with AMD. Your laptop's specs say you have AMD right?

To confirm what you have, please re-post the results of this within CODE Tags:
```

lspci -knnn | grep -A3 -E 'VGA|Display|3D'

```
But even though AMD is opensource drivers, sometimes, depending on the hardware combination, it needs help by using some persistent kernel boot parameters to help it out. That is indicated by what is happening to you now.

I should see that with what that output is...

---

### Post by Keith_Helms on 2024-05-07
> **MAFoElffen said:**
> I'm not sure, meaning "not positive".

Usually that would be required if you had NVidia, but sometimes with AMD. Your laptop's specs say you have AMD right?

To confirm what you have, please re-post the results of this within CODE Tags:
```

lspci -knnn | grep -A3 -E 'VGA|Display|3D'

```
But even though AMD is opensource drivers, sometimes, depending on the hardware combination, it needs help by using some persistent kernel boot parameters to help it out. That is indicated by what is happening to you now.

I should see that with what that output is...

Here's the output from the command:

```
pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 33 [Radeon RX 7700S/7600/7600S/7600M XT/PRO W7600] [1002:7480] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Navi 33 [Radeon RX 7700S/7600/7600S/7600M XT/PRO W7600] [1043:1523]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
--
68:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Phoenix1 [1002:15bf] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Phoenix1 [1043:1523]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

```

---

### Post by MAFoElffen on 2024-05-10
Which Linux kernel? Which release? Which CPU? AMD 8000Z?

Manually upgrade your Linux Firmware to the latest from the kernel.org github page... Do you need instrucytions on how to do that?

Pheonix1 APU was just released and there are patches  from AMD.

---

### Post by Keith_Helms on 2024-05-12
> **MAFoElffen said:**
> Which Linux kernel? Which release? Which CPU? AMD 8000Z?

Manually upgrade your Linux Firmware to the latest from the kernel.org github page... Do you need instrucytions on how to do that?

Pheonix1 APU was just released and there are patches  from AMD.

I've seen this problem with both the Xubuntu 24.04 and Ubuntu Cinnamon 24.04 installs, so that would be the 6.8.0-31 kernel.  My laptop has an AMD Ryzen 9 7940HS w/ Radeon 780M Graphics.

I'm not sure what URL you mean to update the firmware from.  github.com?  [www.kernel.org?]("http://www.kernel.org?")  So yes, I need a bit more detailed instructions.

---

### Post by MAFoElffen on 2024-05-13
This is the original instructions: [https://ubuntuforums.org/showthread.php?t=2489867&p=14154483#post14154483](https://ubuntuforums.org/showthread.php?t=2489867&p=14154483#post14154483)


Here is the updated Instructions to get and install the latest amdgpu firmware
```

cd $HOME/Downloads
wget -N -t 5 -T 10 https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20240410.tar.gz
sudo mv /usr/lib/firnware/amdgpu /usr/lib/firmware/amdgpu-bak
sudo mkdir /usr/lib/firmware/amdgpu
sudo tar -C /usr/lib/firmware/amdgpu linux-firmware-20240410/amdgpu -xvzf linux-firmware-20240410.tar.gz

```
Then reinstall the latest kernel to rebuild the modules:
```

VERSION=$(apt list linux-image-{5,6}* --installed 2>/dev/null | tail -n 1 | awk -F "-" '// {print $3 "-" $4}')
sudo apt install --reinstall -y linux-image-$VERSION-generic linux-headers-$VERSION-generic Linux-modules-$VERSION-generic linux-modules-extra-$VERSION-generic

```

---

### Post by Keith_Helms on 2024-05-13
```
sudo tar -C /usr/lib/firmware/amdgpu linux-firmware-20240410/amdgpu -xvzf linux-firmware-20240410.tar.gz
```

Looks like you combined a couple of commands there.  Can I assume I just need to extract the tar file into /usr/lib/firmware/amdgpu?  Something like the following?
```
cd /usr/lib/firmware/amdgpu; sudo tar -xvzf /home/me/Download/linux-firmware-20240410/amdgpu/linux-firmware-20240410.tar.gz

```

---

### Post by Keith_Helms on 2024-05-13
> **MAFoElffen said:**
> This is the original instructions: [https://ubuntuforums.org/showthread.php?t=2489867&p=14154483#post14154483](https://ubuntuforums.org/showthread.php?t=2489867&p=14154483#post14154483)


Here is the updated Instructions to get and install the latest amdgpu firmware
```

cd $HOME/Downloads
wget -N -t 5 -T 10  https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20240410.tar.gz
sudo mv /usr/lib/firnware/amdgpu /usr/lib/firmware/amdgpu-bak
sudo mkdir /usr/lib/firmware/amdgpu
sudo tar -C /usr/lib/firmware/amdgpu linux-firmware-20240410/amdgpu -xvzf linux-firmware-20240410.tar.gz

```
Then reinstall the latest kernel to rebuild the modules:
```

VERSION=$(apt list linux-image-{5,6}* --installed 2>/dev/null | tail -n 1 | awk -F "-" '// {print $3 "-" $4}')
sudo apt install --reinstall -y linux-image-$VERSION-generic linux-headers-$VERSION-generic Linux-modules*-$VERSION-generic

```

Okay.  I think I followed the instructions

I downloaded the firmware tarfile and extracted it to /usr/lib/firmware/amdgpu using
```
sudo tar -C /usr/lib/firmware/amdgpu --strip-components=2 -xvzf  linux-firmware-20240410.tar.gz linux-firmware-20240410/amdgpu
```

I then reinstalled the kernel using the commands listed except I had to remove the asterisk from **Linux-modules*-$VERSION-generic** because it was pulling in a bunch of NVIDIA modules and giving me errors.

One thing that seemed odd is that previously all the files in the amdgpu  directory had a .zst suffix and the new versions were all .bin files.   Is that correct?

After the reinstall I rebooted and I still get a blank screen if I pass the "splash" option to the kernel.

---

### Post by MAFoElffen on 2024-05-13
Yes. Should be .bin files. Well... Mine is all .bin files.

The reason for the modules =the "*" was to try to also include linux-modules-extra-$VERSION-generic in that reinstall. I edited that podt for you to try to do that command once more.

So what is the results of this posted within Code Tags:
```

grep . /proc/cmdline

```
Add these to /etc/default/grub to change these two lines...
```

GRUB_CMDLINE_LINUX_DEFAULT="--- splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1"
GRUB_GFXMODE=auto

```

---

### Post by Keith_Helms on 2024-05-14
Okay.   I ran the kernel reinstall again and pulled in the  linux-modules-extra version this time.  I then tried rebooting with the  options you listed for GRUB_CMDLINE_LINUX_DEFAULT and no go.  Any time  "splash" is in that list of options I get no video.  If I add just "**radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1**"  without splash Xubuntu 24.04 starts normally.  I can't tell any  difference whether I use those options or not.  As long as splash is not  specified, the OS starts normally.

The output from **grep . /proc/cmdline **is
```
BOOT_IMAGE=/boot/vmlinuz-6.8.0-31-generic  root=UUID=8a7cf40f-502d-46c5-9ce4-897eee0bb848 ro noresume quiet  radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1
```

At this point I'm willing to live without splash in the grub defaults.   Unless you're just curious and want to try something else, Xubuntu 24.04  seems to be working with no major problems other than that. 

Getting Mint and Ubuntu working with this new laptop hardware has been a work in progress.

1. When I tried to install Xubuntu 22.04/Mint 21 on it, the default 5.15  kernel didn't recognize the keyboard or touchpad.  I had to use a USB  keyboard and mouse to complete the install and then installed the  linux-oem-22.04d package to pick up the 6.5 kernel.  That got the  keyboard and touchpad working.  The remaining problem was I could not  switch the video resolution from the default 2560x1600.  Any other  resolution resulted in corrupted graphics.
2. I installed Xubuntu 23.10 which came with the 6.6 kernel and that  allowed me to switch display resolutions, but of course that was a test  release.
3. With 24.04 and 6.8 I can switch display resolutions and have no  obvious video problems other than that stupid splash option crashing  something under the covers.

Thanks for your help in trying to resolve this!

---

### Post by MAFoElffen on 2024-05-14
I have one more idea...

Since "splash is what is crashing it (which doesn't make sense)... How about if we try to set basic video mode in the early boot from Grub?

At the Grub2 Menu, press the <C> key. > At the Grub prompt, Type the work (without the single quotes) 'videoinfo' Press the <Enter> key.

Write down the resolution that you can live with. (for the boot process, any messages, and the Splash screen). That is what Grub says it sees as valid resolutions for the BIOS, GPU, and Display. Lets say, for example it said and you chose "1920x1080x32"

After that, press the <Esc> key... That will return you back to the Grub Menu. Boot.

Edit file /etc/default/grub with elevated previledges, and change these lines to this:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"
GRUB_GFXMODE=1920x1080x32

```
Save and exit.

Do this to pickup the changes:
```

sudo update-grub

```
That will try to set the boot process' graphics to a known mode. If it doesn't work, we at least ruled that out, right?

If it doesn't work, then file a bug report against "plymouth"

---

### Post by Keith_Helms on 2024-05-16
> **MAFoElffen said:**
> I have one more idea...

Since "splash is what is crashing it (which doesn't make sense)... How about if we try to set basic video mode in the early boot from Grub?

At the Grub2 Menu, press the <C> key. > At the Grub prompt, Type the work (without the single quotes) 'videoinfo' Press the <Enter> key.

Write down the resolution that you can live with. (for the boot process, any messages, and the Splash screen). That is what Grub says it sees as valid resolutions for the BIOS, GPU, and Display. Lets say, for example it said and you chose "1920x1080x32"

After that, press the <Esc> key... That will return you back to the Grub Menu. Boot.

Edit file /etc/default/grub with elevated previledges, and change these lines to this:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"
GRUB_GFXMODE=1920x1080x32

```
Save and exit.

Do this to pickup the changes:
```

sudo update-grub

```
That will try to set the boot process' graphics to a known mode. If it doesn't work, we at least ruled that out, right?

If it doesn't work, then file a bug report against "plymouth"

No luck with that either.

When I boot with splash and remove quiet the messages always end with
```
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ...
```

I don't know if that might give a clue where it's failing.

---

