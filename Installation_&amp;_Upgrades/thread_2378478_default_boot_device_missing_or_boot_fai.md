---
title: "default boot device missing or boot fai"
date: 2017-11-23
forum: Installation &amp; Upgrades
---

### Post by carsten77 on 2017-11-23
notebook with dualboot Ubuntu&Windows 10 is showing bluescreen with message default boot device missing or boot failed
boot repair disk cant fix it, giving me this text [http://paste.ubuntu.com/26028934/](http://paste.ubuntu.com/26028934/)

---

### Post by yancek on 2017-11-23
Your boot repair link shows a GPT drive (the 1TB drive) which with windows on should be an EFI install of windows.  There should be an EFI partition at the beginning of the disk for EFI files and there is NOT.  You have only one partition on that disk which is a windows ntfs partition.  There is no sign of any Ubuntu/Linux system on that drive.  Some info on what happened just prior to this occurriing might be helpful but as is there is nothing there for boot repair to repair.

---

### Post by carsten77 on 2017-11-23
right before this happened the Ubuntu system broke down while working. I have a 110 GB system hard drive that has an Ubuntu and a Windows partition plus the 1TB drive for data.

---

### Post by yancek on 2017-11-23
What does "broke down" mean?  Specifics.  Boot repair shows only the 1TB drive and a 16GB drive which I suppose is the flash drive you are using.It shows /dev/sdb as 20MB in size (Haven't made those for 30 years?) which I doubt is correct.  Probably your 110GB drive and it shows Invalid MBR signature found.  Not sure what to do about that although if you can post more details on what exactly happened before this problem someone may have a suggestion.

---

