---
title: "Help need with boot repair boot info summary included!"
date: 2023-03-23
forum: Installation &amp; Upgrades
---

### Post by se7enpop on 2023-03-23
I have an HP laptop with dual boot for windows 11 and ubuntu 18 and it has been working well untill today when i have updated ubuntu
An error appeared when i was booting and the laptop booted directly to windows no grub menu appeared then when i searched for the error i found this [https://askubuntu.com/questions/1122261/unexpected-return-from-initial-read-volume-corrupt](https://askubuntu.com/questions/1122261/unexpected-return-from-initial-read-volume-corrupt) and followed the first answer first two step with no success 
Now i have installed boot repair on a live ubuntu USB and extracted the boot info report to a paste bin [https://pastebin.ubuntu.com/p/QdBxwgjWXR/](https://pastebin.ubuntu.com/p/QdBxwgjWXR/)
Can any expert help me to decide if i should use the recommended repair or not

---

### Post by oldfred on 2023-03-23
Note that 18.04 reaches EOL soon.
The 'main' archive of Ubuntu 18.04 LTS will be supported for 5 years until [April 2023]("https://wiki.ubuntu.com/Releases").
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

Did you always have UEFI Secure boot on? Line 122 & line 265 shows generic kernel
Windows updates often also update UEFI which reverts it to defaults.
You have to go back and make any changes you made to install Ubuntu.
Report mentions both nVidia & AMD? line 115 or a bug in report?

Is f12 latest UEFI from HP for your model? Line 120

HP typically requires you to go into UEFI settings (not menu) to change boot order.
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

Windows updates may also turn fast start up/hibernation back on and then grub may not boot Windows.

---

### Post by se7enpop on 2023-03-23
Hi and thanks for replaying 
my answer is in [COLOR=#ff0000]red[/COLOR]

Did you always have UEFI Secure boot on? Line 122 & line 265 shows generic kernel

[COLOR=#ff0000]No I didn't it was always was disabled but it appears it has been enabled and I have re-disable it now and it shows me the following error while booting 

[B]Invalid Image
Failed to read header: unsupported
Failed to load image: unsupported
start_image() returned unsupported[/B]
 
then continue booting to windows

keep in mind that it was not the first error I have faced 
the first error was
[/COLOR][COLOR=#ff0000][B]Unexpected return from initial read: Volume Corrupt 
buffersize 1000 Failed to load image \EFI\ubuntu\grubefi: Volume Corrupt  start_image() returned Volume Corrupt[/B]

but then a ran a couple of command to try to fix the error 

sudo fsck -f /dev/XXXX  where XXXX the string of Linux file system I found using sudo fsck -l
then I ran sudo fsck.fat -a /dev/XXXX where XXXX is the string of EFI partition 
i think after the last command I got my current error 
[/COLOR]
Report mentions both nVidia & AMD? line 115 or a bug in report?
[COLOR=#ff0000]My labtop has an AMD CPU AMD Ryzen 7 5800H with Radeon Graphics and a NVidia GPU NVIDIA GeForce RTX 3060 Laptop GPU 

[/COLOR]Is f12 latest UEFI from HP for your model? 
[COLOR=#ff0000]I don't know:KS[/COLOR]

---

### Post by oldfred on 2023-03-23
See if this shows version. You also can just boot into UEFI settings & see version somewhere. And then on HP's site for your model, should be UEFI/BIOS updates.
sudo lshw | grep -m 1 -A 5 "*-firmware"

So does Windows boot ok, and it just Ubuntu that does not.
Those errors seem to be more from UEFI??

My Dell with Intel 11th Gen chip installed Ubuntu 22.04 even though Secure boot was on. I did have to turn fast start up and bitlocker off.
If system supports Windows 11, better to use more current Ubuntu version to have latest kernel & drivers.

---

### Post by tea for one on 2023-03-24
Line 248 - /dev/nvme0n1p6           4.9G available   90% used 

Your Ubuntu partition has very little free space and would benefit from some housekeeping.

---

### Post by se7enpop on 2023-03-24
I have been able to use a preinstalled HP tool to check for bios firmware update and it is stating that all drivers are up to date.

And Yes windows boot is okay the problem is with ubuntu.

You are right about the need to update ubuntu to the latest version and I will consider it in the future but in the meanwhile I need to be able to log in ubuntu so could I safely run the Recommended Boot Repair form the boot repair tool based on the Boot info summary I provided or not and if not could you please tell me what is the best course of action.

I really appreciate your time and effort.

Thanks.

---

### Post by se7enpop on 2023-03-24
Yes sure once I login house keeping is my Frist priority

---

### Post by oldfred on 2023-03-24
Boot-Repair does not require you to boot into system.
It typically updates grub or does a total reinstall of grub. You can do a full reinstall of grub & latest kernel from Boot-Repair's advanced mode.

More important is to be able to mount your Linux partitions and have good backups of the data.

Can you press escape when booting just after vendor logo & get grub menu? And then boot recovery mode to a command line.

---

### Post by tea for one on 2023-03-24
> **se7enpop said:**
> but in the meanwhile I need to be able to log in ubuntu so could I safely run the Recommended Boot Repair form the boot repair tool based on the Boot info summary I provided or not and if not could you please tell me what is the best course of action.

You can run the boot-repair utility from a live session (no need to log in)
As you can still boot into Windows, it's probably worth a shot.

Alternatively, do you have a UEFI shell, which will allow you to find and run EFI\ubuntu\grubx64.efi

Lastly, you can create a rEFInd Boot manager installed on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
I keep a USB with rEFInd for emergency use because it has a knack of finding and booting an OS (in the rare situation where Grub has proved to be stubborn)

---

### Post by se7enpop on 2023-03-24
@tea for one I know I already ran boot repair form a live session this how i got the boot info summary in the first place I'm now following boot repair recommendation to share the info summary here so someone with experience could help me decide if i can run the recommended boot repair action or not 
@oldfred no i cant escape brings up the hp pause menu showing the the bios shourtcut key maps

---

### Post by se7enpop on 2023-03-24
I think I'm going to run the boot repair from the live session anyway

---

### Post by se7enpop on 2023-03-24
Thanks a lot Guys Boot repair fixed the problem

---

