---
title: "2 HDDs: One with Windows 10 and one with Ubuntu Server: How to select boot option?"
date: 2020-01-27
forum: Installation &amp; Upgrades
---

### Post by james_n2 on 2020-01-27
Hello everyone,
My situation is a little bit different. I have a dell PC that I install 1 extra hard drive in addition to the stock one. The original hard drive has Windows 10 Pro on it.
I just installed Ubuntu server 18.04 LTS on the newly added Hard drive.
Now the system will just boot directly to the Ubuntu Server whenever it turns on. If I press "Esc" key, then I get a blank command prompt in the GRUB screen.
I have seen that if you install Ubuntu on the same hard drive of the Windows, you will get a screen with a list of options such as: 

Ubuntu
Advanced Ubuntu
Windows Boot manager
....

But I don't have this option list in my case
Could I please ask if anyone know how I can select with OS to boot/start with?
Thank you very much for your helps
James

---

### Post by oldfred on 2020-01-27
Since Windows pre-installed it would be UEFI on a gpt partitioned drive.

Did you install Ubuntu on a gpt partitioned drive in UEFI boot mode.
If Ubuntu is  UEFI this will add Windows to grub menu.
sudo update-grub

UEFI and BIOS are not compatible. If you have that you can only boot from UEFI boot menu.
If drive is gpt with BIOS install you can convert to UEFI with grub reinstall ( and first adding an ESP). But if MBR, better to start over and use gpt.

---

### Post by james_n2 on 2020-01-27
If I go to BIOS setting, under the Boot sequence, I see ubuntu and HDD (the drive where I installed Windows 10)
Even though I select ubuntu as 1st choice, HDD as 2nd choice, it still did not display the boot menu...
Do you have something like step-by-step guide to check on these?
Thank you very much

---

### Post by Impavidus on 2020-01-28
Have you disabled FastStartup in Windows? It may be enabled again automatically when Windows installs updates. With FastStartup enabled the Ubuntu tools cannot detect Windows and won't make an entry for it in the grub menu.

---

### Post by yancek on 2020-01-28
The steps you describe in post 3 aren't going to change anything except the one time boot.  You didn't answer the questions asked in post 2.  Answers to those questions would help someone to help you.  First need to verify that you do have an EFI install on a GPT partition.  If you are able to boot Ubuntu, open a terminal and run this command and post the output:

```
sudo parted -l
```

It isn't clear from your post if you can boot either Ubuntu or windows from the BIOS firmware you describe, can you?  You need to mount the efi partition and look at it to see if you have both windows and ubuntu directories there because if you have no ubuntu files in efi, you won' be able to boot windows from the Grub boot menu even if it was there.

---

