---
title: "Ubuntu Inside Windows on a Thumb Drive"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by thatone1guy on 2011-02-26
Hi,I have Windows 7 running on a laptop, and I would like to dual boot Ubuntu on it. There is not enough space on the hard drive however, I have a thumb drive that has enough space to run it that I am not using. I clicked the button that said "Install inside Windows" and I installed it to the thumb drive. After that finished I rebooted my computer, and on the start up I can choose between booting Windows and Ubuntu. Windows boots fine, however when trying to boot Ubuntu I get an error message saying that it can't find the file(or it is corrupt) ubuntu/winboot/wubildr.mbr the status is 0xc000000e.I looked for the file, and it is there. Is there any way to fix this?

Thanks in advance,
Michael

---

### Post by mike555 on 2011-02-26
if you installed "inside"  Windows I don't think you installed into your thumbdrive  (because Windows isn't on your thumbdrive)you might check Windows add/remove and see if Ubuntu is there .......

---

### Post by thatone1guy on 2011-02-26
Yes, I checked and it is an installed program.

---

### Post by Mark Phelps on 2011-02-26
The file that wubi uses for Ubuntu is most probably on the thumb drive; Windows is on the internal hard drive.

So, are you saying that with the thumb drive inserted you still can't launch Ubuntu?

Is this from the selection menu that Windows displays?

Can you still launch Windows OK?

---

### Post by thatone1guy on 2011-02-26
yes, With the thumb drive inserted I can not launch Ubuntu from the window that Windows displays on the startup, however Windows still works fine.

---

### Post by bcbc on 2011-02-26
> **thatone1guy said:**
> Hi,I have Windows 7 running on a laptop, and I would like to dual boot Ubuntu on it. There is not enough space on the hard drive however, I have a thumb drive that has enough space to run it that I am not using. I clicked the button that said "Install inside Windows" and I installed it to the thumb drive. After that finished I rebooted my computer, and on the start up I can choose between booting Windows and Ubuntu. Windows boots fine, however when trying to boot Ubuntu I get an error message saying that it can't find the file(or it is corrupt) ubuntu/winboot/wubildr.mbr the status is 0xc000000e.I looked for the file, and it is there. Is there any way to fix this?

Thanks in advance,
Michael
I think that error is "no such device". Wubi boots by the Windows Boot Manager calling grub4dos (wubildr.mbr) and then grub4dos chains into grub2 ..... to Ubuntu.
So likely Windows Boot Manager cannot see the thumb drive.

What the reason for that is - I can't say.

---

### Post by thatone1guy on 2011-03-04
Hi,I have Windows 7 running on a laptop, and I would like to dual boot Ubuntu on it. There is not enough space on the hard drive, however, I have a thumb drive that has enough space to run it that I am not using. I clicked the button that said "Install inside Windows" and I installed it to the thumb drive. After that finished I rebooted my computer, and on the start up I can choose between booting Windows and Ubuntu. Windows boots fine, however when trying to boot Ubuntu I get an error message saying that it can't find the file(or it is corrupt) ubuntu/winboot/wubildr.mbr the status is 0xc000000e.I looked for the file, and it is there. Also, I checked in the list of installed programs, and there is one called Ubuntu. Is there any way to fix this?

Thanks in advance,
Michael

---

### Post by Rubi1200 on 2011-03-04
Hi and welcome to the forums :)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

This will help us get a better overview of your current setup. It will make offering solutions easier.

Thanks.

---

### Post by thatone1guy on 2011-03-05
I can not get to that screen. When I boot from a thumb drive it just lets me choose which OS to boot (with only windows actually working). Also, it tells me to remove any disks or other media, which I must ignore.

---

### Post by thatone1guy on 2011-03-05
After using unetbooting-windows, I installed it to the thumb drive, and now I can not run any OS. I now get an error saying no such device:937dab01-ee7c-48ea-8e0f-4d4211c1873. How can I fix this?

---

### Post by thatone1guy on 2011-03-05
I want to install Ubuntu on a thumb drive, while not effecting Windows which is already installed on the computer.I used unetbooting-windows to do this. I installed ubuntu to the thumb drive, and now I can not run any OS even after booting from the hard drive. I an error saying no such device:937dab01-ee7c-48ea-8e0f-4d4211c1873, and I can type something in next the the grub rescue> prompt. How can I fix this?

---

### Post by lisati on 2011-03-05
Threads merged.

---

### Post by thatone1guy on 2011-03-05
Okay, I fixed the grub rescue problem and can now run windows 7 again, however Ubuntu still isn't working. Oh well, it was just a free computer that only had 16gigs memory anyways, so I might just forget about dual booting.

---

