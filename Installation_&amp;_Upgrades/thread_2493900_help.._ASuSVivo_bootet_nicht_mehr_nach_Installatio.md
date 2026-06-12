---
title: "help.. ASuSVivo bootet nicht mehr nach Installation-efi not found"
date: 2023-12-28
forum: Installation &amp; Upgrades
---

### Post by julia7threepwood on 2023-12-28
I was installing ubuntu 18.04 bionic onto a ASUS VivoBook Modell S533F with Windows (I think 10).
I used an usb stick.
In the installation routine I chose to create a / and a /home partition and a swap partition. Then I was asked to add an EFI Partition. I cancelled the / partition and added space of 800MB for the EFI Ppartition and after I used the rest again for the / partition. Then the routine went on and Iwas asked to shut down the computer. So I took the stick out and it shut off. 

Now it doesn't boot at all. Without the stick I only land in BIOS. I don't know what to put in there. There is no path for booting at all under the boot section. And I don't know what path to create.

When I use the bootstick again although with this one I cannot boot anymore. There comes a thread like this:

Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\\mmx64.efi: Not Found
Failed to start MokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed: Not Found



:(
What can I do?
The stick works still on my thinkpad without problems. I can boot from there, Icould install ubuntu and I started the live-version. no problem.

Waht did I do to the ASUSVivobook? How can I recover it? And in case just to reinstall again?

---

### Post by Rubi1200 on 2023-12-28
Hi and welcome to the forums :-)

I am trying to get my head around what you have tried here.

Please pay attention to the following points:

1. 18.04 has reached EOL and is no longer supported. Please consider a more recent LTS version such as 20.04 or better still 22.04

2. were you trying to install Ubuntu as a dual-boot with Windows, in other words with Windows, or did you choose to install Ubuntu on the whole drive?

3. if you have a newer laptop I assume it is UEFI and not legacy BIOS. If so, you need to start the installer also in EFI mode; did you do that?

4. to help us, please run the boot info script from the liveUSB and choose to create a summary report. The link is in my signature. Choose to create the report and post the link to the pastebin back here on the forum

I am sure we can help you get this sorted out, but it may take a few steps.

---

### Post by julia7threepwood on 2023-12-28
Thank you for your answer.
1.Yes, I see, its an older version.. I didn have the right capacity on a stick and chose 18.4 .. :/ naja on my thinkpad it works great. I was hoping to upgrade it later..
2. I wanted to use the entire drive for ubuntu. thats why i chose the partitions. i don't use windows since many years and had no use for it.
3. mm.. I am sorry, I don't actually know.
4. I will try to find this information.. what I understand, that I can run "boot-repair" from a shell, when I am in a live-session? 
I can do that on my other computer. But does the result help me for the Asus? On Asus the stick doesn't boot anymore.. :/

I try my best, thanks for your patience

---

### Post by Rubi1200 on 2023-12-28
Perhaps I misunderstood something.

If you boot the Asus without the stick you only get to BIOS and cannot do anything correct?

What happens if you boot the Asus with the stick? Where does it take you to?

If you have the option to Try Ubuntu then you can run the script I mentioned before.

---

### Post by julia7threepwood on 2023-12-28
[IMG]https://www.file-upload.net/download-15245579/signal-2023-12-28-211518_002.jpeg.html[/IMG][IMG]https://www.file-upload.net/download-15245580/signal-2023-12-28-211712_002.jpeg.html[/IMG][IMG]https://www.file-upload.net/download-15245581/signal-2023-12-28-212818_002.jpeg.html[/IMG][IMG]https://www.file-upload.net/download-15245583/signal-2023-12-28-213724_002.jpeg.html[/IMG][IMG]https://www.file-upload.net/download-15245582/signal-2023-12-28-214458.jpeg.html[/IMG]

Here I made some pictures from the BIOS of the ASUS. I hope it helps. There are no path's whatshoever to any bootable devices.. From your answer I understand that I should try to create a new bootstick? Now I have my other computer with ubuntu on it. so I have to use another tool than rufus. Then I have to give it certain informations for the bootsystem of the asus, right? Can you tell me from the pictures, what I have to think about?

Thank you.

---

### Post by julia7threepwood on 2023-12-28
[https://share.riseup.net/#yxLeEv59UtEPmNeYFT7w9g](https://share.riseup.net/#yxLeEv59UtEPmNeYFT7w9g)

[https://share.riseup.net/#icM2wl9Mlm5liRgsT4Rg1g](https://share.riseup.net/#icM2wl9Mlm5liRgsT4Rg1g)

[https://share.riseup.net/#tpHN3pj5H_UtafcPM4jdHQ](https://share.riseup.net/#tpHN3pj5H_UtafcPM4jdHQ)

I tried to take some fotos of the bios in that ASUS

---

### Post by julia7threepwood on 2023-12-28
Yes, with the stick I only get the following:

Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\\mmx64.efi: Not Found
Failed to start MokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed: Not Found

without the stick I land in the bios.

---

### Post by julia7threepwood on 2023-12-28
I chose now to get yumi and I am trying to create a bootable stick with the boot-repair-disk that you mentioned. Maybe it helps..

---

### Post by jeremy31 on 2023-12-28
I am not sure if Yumi is still supported, the Ventoy program works great, you just install Ventoy to a stick and copy/paste the ISO onto the USB

---

### Post by julia7threepwood on 2023-12-28
Dear Rubi1200,

I managed to create a new bootstick, now with xubuntu 22.04.3 . The ASUS accepted it. I did another installation but same as before I only end up in the BIOS after restart.
But I can still use the live-system and could run boot-repair.
I made a report and put it in the bin:

[https://paste.ubuntu.com/p/XRGdkBpWhN/](https://paste.ubuntu.com/p/XRGdkBpWhN/)

Thank you for further councelation..

Julia.

---

### Post by ian-weisser on 2023-12-28
The ASUS VivoBook Modell S533F* series all come with Optane.

Looks like you did not disable the Optane RAID. Was that intentional?

Possible RST vs AHCI conflict.

---

### Post by MAFoElffen on 2023-12-29
I see the Intel Optane sticks in the report showing up as:
```

nvme0n1:29.3GB:nvme:512:512:unknown:INTEL HBRPEKNX0202AO:;
nvme1n1:512GB:nvme:512:512:gpt:INTEL HBRPEKNX0202A:;

```
There is a way to make that work, but is a very advanced installation. Much easier to install with both of the Intel RST Optane modules disabled in the BIOS, the BIOS SATA mode set to AHCI, with the modules physically removed...

To boot "only" Linux with Optane is possible to install and configure... There is a lot of manually typed sets in terminal. I've done it with this guide:
[https://codenotary.com/blog/ubuntu-how-to-use-intel-optane-memory-for-ssd-caching](https://codenotary.com/blog/ubuntu-how-to-use-intel-optane-memory-for-ssd-caching)

It is not something that I would say would be recommended for a beginner or someone new to Linux to try to set up.

What is your choice on that?

---

### Post by julia7threepwood on 2023-12-29
Thank you, MaFoElffen,

I see.. ok, I try to translate for my understanding..
1. I can now try to enter the BIOS and change the settings in the SATA panel to AHCI. And see if it works..
2. You suggest I could reinstall xubuntu on a shell somehow before the system? I will read the guide first ;) but you're right, sounds quiet advanced to me.
3. I have to say, weather Optane nor RAID does tell me anything. I will have to learn a lot to understand that.

---

### Post by julia7threepwood on 2023-12-29
I changed the settings in the SATA panel to AHCI.  It worked !!!! So easy in the end. Incredible :grin:

---

### Post by MAFoElffen on 2023-12-29
Yes, to do without the RST Optane (high-tech disk cache):
Enter the BIOS and turn off Intel RST (Optane). I couldn't find the ASUS instructions. Intel had these:
```

Enter the BIOS with Del or F2 keys during the boot process.
Locate the SATA or VMD Controller Management page.
    SATA: Change from RST Premium to AHCI.
    VMD: Change from VMD Enabled to Disabled.

```
What I know, with helping others with this, if you re not going to setup it up, and have it off instead, then you have to physically remove the Optane module from their slots. It not, even if you disable it in the BIOS, it has to be removed, to not be seen.

This yuotube video goes over that. [https://www.youtube.com/watch?v=qdVNMHF1WrI](https://www.youtube.com/watch?v=qdVNMHF1WrI)
Removing those modules is at 2:23 and 2:30. You do not have to physically remove the battery like they show to remove or replace just those, but "you do" have to unplug the battery power cable shown at 2:02...

The first one is purely Optane... The one that says 32GB... And Intel does not recommend using them as Storage Devices. The number on that is "INTEL HBRPEKNX0202A". The other drive is a 512GB PCIe M.2 NVMe drive. The optane drive can be replaced with an up to 4TB M.2 PCIe m-key SSD drive.

---

