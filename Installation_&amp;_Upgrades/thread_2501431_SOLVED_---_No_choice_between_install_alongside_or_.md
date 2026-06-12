---
title: "SOLVED --- No choice between install alongside or instead of windows"
date: 2024-10-07
forum: Installation &amp; Upgrades
---

### Post by peter20p on 2024-10-07
I try to install ubuntu studio 24.04 on a windows 11 pc. When the question "How do you want to install Ubuntu Studio" appears, no choice of answer is displayed. I install from an usb key. In the bios, I disabled the secure boot option.

---

### Post by tea for one on 2024-10-07
Can you use your usb key and boot into a "Try Ubuntu" live session?
Open a terminal and enter:-
```
sudo parted -l
```
Please post the command and output within code tags (for legibility)

---

### Post by yancek on 2024-10-07
Do you not see the option to Erase Disk and install Ubuntu?  That is pretty much always there.  Did you verify the download before writing to the usb as it is possible for the iso file to be corrupted  when being downloaded?  Posting the output of the command suggested should answer some questions like did you create unallocated space on the drive before booting the Ubuntu USB, do you have the default hibernation setting in windows off?

---

### Post by peter20p on 2024-10-07
Thanks. It answers parted invalid option 1

---

### Post by jeremy31 on 2024-10-07
It isn't a 1 but a small L, best to copy/paste terminal commands, you can paste in terminal using right click options

---

### Post by Rubi1200 on 2024-10-07
It would also be helpful if you can tell us what you used to write the ISO to USB. Etcher, Rufus, Ventoy, something else?

Another important thing: did you write the ISO to boot in EFI mode?

---

### Post by yancek on 2024-10-07
If you copy/paste the command and get the necessary output, could you also answer the other questions asked in earlier posts so we have more details?

---

### Post by peter20p on 2024-10-09
Problem is solved. We reformatted the drive before installation and everything went OK.

---

