---
title: "Boot-repair for 24.04.1 not working grub-efi partition error"
date: 2024-11-07
forum: Installation &amp; Upgrades
---

### Post by pratibhapotla on 2024-11-07
[https://paste.ubuntu.com/p/4Q2W65wkZT/](https://paste.ubuntu.com/p/4Q2W65wkZT/)

Hi Ubuntu team,

After upgrading to 24.04.1 LTS, my system has gone for a toss. There is no GUI and after testing multiple solutions online, here I am trying to run boot-repair using a live USB using the boot-repair software provided by the community. 

However, when I run "Recommended repair" button, it throws an error stating "Please enable a repository containing the [grub-efi] packages in the software sources of unknown Linux distribution (/dev/sda3). Then try again". I have also provided the paste bin information above. I have a critical project waiting for me to start but this OS version has been giving sleepless nights since few days.

Looking forward for help. Please let me know if you require any other information.

P.S. I have been using Ubuntu since 2010 and I have had to post something like this only in 2024 for the first time ever. 

Thank you,
Pratibha

---

### Post by oldfred on 2024-11-07
Is this Ubuntu or Mint?
It says live installer running Boot-Repair is Mint.

What brand/model system?
Have you installed nVidia driver?
Can you boot recovery mode?

---

### Post by pratibhapotla on 2024-11-07
Hi Oldfred,

Thank you for your quick reply. Even I got confused with this. 

1) I made a bootable ubuntu USB using Etcher software on a MacBook Air laptop since that was the only other machine I had access to. And the system I have is a Dell Precision Tower 5820 with 8 cores and 32 GB RAM with Ubuntu OS.
2) I struggled with NVIDIA driver installation and uninstallation many times since for 24.04 LTS, I read on multiple forums, it should be uninstalled with Wayland related problems. 
3) I can't boot into recovery mode as it says "no hostname set" and also throws an error "FAILED to start systems-login.service - User login management".

So my only option was to try boot-repair. What could I do next?

Thank you,
Pratibha

---

### Post by oldfred on 2024-11-07
If install is Ubuntu and live installer Mint that is some of problem.
Mint is not an official flavor of Ubuntu and has many modifications, even though based on Ubuntu.
Flavors
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

---

### Post by yancek on 2024-11-07
Since you have tried multiple solutions and we don't know what they were, it is difficult to make suggestions.  /dev/sda1 is your EFI partition which appears to have the necessary files.  /dev/sda2 is a vfat partition with only grub.cfg in it so that is useless.  /dev/sda3 is your / filesystem partition for Ubuntu and boot repair shows on line 87 that it has no fstab.  In addition to the message you posted "no hostname set" and also throws an error "FAILED to start systems-login.service - User login management" you might try reinstalling and select to NOT format sda3.  If you have personal data on that partition, back it up as a precaution but it should not be overwritten.

---

### Post by pratibhapotla on 2024-11-08
Thank you, oldfred and yancek for the details.

oldfred: When I changed the boot sequence in BIOS settings for loading the live USB, I saw two occurrences of the USB with the boot-repair (I don't know why), so I randomly selected one of them. I will retry this step by selecting the other one and check if it shows Ubuntu now instead of Mint.

yancek: Yes, I do have personal data on /dev/sda3 partition. I was trying to solve this first by boot-repair and keep reinstalling the OS as the last resort. 

I will post an update if I am able to resolve this. 

Kindly,
Pratibha

---

### Post by oldfred on 2024-11-08
You should not be selecting randomly a USB boot entry.
Most flash drive installers create a USB with both old BIOS and newer UEFI boot. Systems since 2012 are UEFI, so almost all should be booting in UEFI mode.
One time boot should clearly show UEFI as an option.
Some have BIOS boot menu & then a UEFI boot menu.
Others just show UEFI:XXX or XXX where XXX is name or label of flash drive. You always want the UEFI option.

How you boot install media for both Windows & Ubuntu UEFI or BIOS is then how it installs or repairs. You must always be consistent.

New systems starting in 2020 are UEFI only.
My Dell with Intel 11th Gen chip says "BIOS" but once in BIOS it says UEFI only.

---

### Post by tea for one on 2024-11-08
> **oldfred said:**
> Others just show UEFI:XXX or XXX where XXX is name or label of flash drive. You always want the UEFI option.
How you boot install media for both Windows & Ubuntu UEFI or BIOS is then how it installs or repairs. You must always be consistent.
New systems starting in 2020 are UEFI only.
+1 to all of the above

@pratibhapotla
It can be confusing if you are unaware of the consequences.
I've attached an image to show the two choices.

---

### Post by pratibhapotla on 2024-11-08
Thank you for all detailed replies. I will try again with the way you both mentioned and post my update here soon.

---

### Post by pratibhapotla on 2024-11-14
Hi team,

Sorry for the delay. I had some pressing work to be completed first on a standby system. 

I have done a fresh start by creating a USB having Ubuntu 24.0.1 LTS desktop ISO image on it to boot my Ubuntu desktop. It is not showing Mint now!

After clicking on "Try Ubuntu" and running boot-repair, I get the same error as the title of this ticket. Following is the [paste bin info]("https://paste.ubuntu.com/p/Ch3vVNGqKG/"). What step can I take next or shall I just click on "Install Ubuntu" and re-install? I have a lot of unbacked data but I will be able to manage if I lose it.

Thank you,
Pratibha

---

### Post by tea for one on 2024-11-14
> **pratibhapotla said:**
> After clicking on "Try Ubuntu" and running boot-repair, I get the same error as the title of this ticket. Following is the [paste bin info]("https://paste.ubuntu.com/p/Ch3vVNGqKG/"). What step can I take next or shall I just click on "Install Ubuntu" and re-install? I have a lot of unbacked data but I will be able to manage if I lose it.
While you are in a "Try Ubuntu" session, why not back up your data before you lose it?

---

### Post by pratibhapotla on 2024-11-14
Thank you for replying tea for one. So for that, shall I just plug in another USB and copy using terminal?

---

### Post by tea for one on 2024-11-14
> **pratibhapotla said:**
> Thank you for replying tea for one. So for that, shall I just plug in another USB and copy using terminal?
Yes, indeed, via the terminal or the file manager.

yancek (post 6) mentioned that your fstab file is missing from the first boot-repair report.
It is also missing from the later report (see line 90) - do you know why it is missing?

---

### Post by pratibhapotla on 2024-11-14
Tea for one - thank you for replying. 

I have done a lot of things to make the GUI appear for this version of OS and I'm not sure what could have messed the fstab file. Any suggestion from your side would really help me. I am about to re-install the OS since the repair also looks complicated to me. I am not that experienced in these issues. Apologies for these naive questions.

Kindly,
Pratibha

---

### Post by grahammechanical on 2024-11-14
May I say something? We seem to have moved away from the original problem.

> There is no GUI an

Boot Repair does not fix the OS not loading to a GUI - Login screen and desktop. Boot Repair will re-install certain Grub boot files into the EFI System Partition (sda1). Will anything change? I do not think so. And then there is this:

> 3) I can't boot into recovery mode as it says "no hostname set" and also  throws an error "FAILED to start systems-login.service - User login  management".

@pratibhapotla

It seems that you can access the Grub boot menu. Can you select Advance Options for Ubuntu? I think you can. Otherwise you would not say "I can't boot into recovery mode." I think you can boot into recovery mode. By the time we are at the recovery menu Linux has loaded. No need to use Boot Repair. What recovery options are you choosing?

Select Resume to load to a login screen and desktop without using the proprietary video driver (Nvidia). You will be using an open source video driver (Nouveau). If that is successful open Software and Updates>Additional Drivers tab and disable the proprietary driver. Continue using the open source video driver.

> as it says "no hostname set"

I do not know what that means. But as a wild guess. If we choose Recovery Menu>Network the friendly recovery utility will set up an internet connection using settings in the OS. If we are not connected to a modem that is connected to an Internet Service Provider we might get that message. Or, if we are trying to connect the machine to a local network and the correct settings are not in the OS. I do not know. I am just guessing.

I am concerned. From what you have posted here, I am concerned that if you re-install Ubuntu you might create a bigger mess than you are now in. I am guessing that you have tried so many repair attempts that the information that you have provided is no longer applicable. We are offing advice that does not fit the current situation.

Please go back to the beginning and tell us the situation. Or, re-install after backing up the documents that you do not want to lose. And do not select to have Third Party Software installed. That will bring in the Nvidia driver and you will be back to where you started from.

Regards

---

### Post by pratibhapotla on 2024-11-14
Thank you, grahammechanical for your detailed reply.

I was initially able to get into recovery mode, which is where I used multiple advices to fix the no GUI problem and then suddenly it started to show a black screen with cursor blinking. Post that, whenever I select recovery mode for the selected linux kernel (6.8.0.48-generic), it throws error "set to friendly-recovery" target and then hangs there. Nothing happens - which is why I thought I could try boot-repair. 

From the fear of messing up even more, is it better I re-install using the live ISO image? 

Thank you for taking the time to reply, really appreciate inputs from everyone!

---

### Post by yancek on 2024-11-14
> I used multiple advices to fix the no GUI problem 

When you have a problem, make not of exactly what it is and if you try any repairs/changes, make detailed notes of that also so you have information to use if you post for help.  You might try reinstalling and selecting NOT TO FORMAT the / and /home partition if you have one.  I've reinstalled Linux on an unbootable system and selected to NOT format and have done this multiple times successfully.

---

### Post by pratibhapotla on 2024-11-14
Hi Yancek and everyone else who tried to help. I will definitely make note of each step next time anything like this happens.

I tried to save the data on the system but manual partitioning options during re-install looked too complicated so went ahead and erased the data and re-installed the OS. Everything looks great as of now. I did UNSELECT the NVIDIA third-party software installation. Hoping that it does not crash later. 

Marking this as Solved.

Kindly,
Pratibha

---

