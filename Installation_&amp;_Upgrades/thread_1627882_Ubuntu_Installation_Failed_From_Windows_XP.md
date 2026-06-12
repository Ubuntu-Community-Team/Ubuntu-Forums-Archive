---
title: "Ubuntu Installation Failed From Windows XP"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by BParkoff on 2010-11-21
I downloaded latest Ubuntu version 10. I bruned it to CD disc. I run WUBI.exe. Some files copied to the hard drive, but the error message interrupted in the middle of the installation process. It said unable to install -- permission denied.
 
I don't see what is wrong. My Windows XP is full administration control. All the files should be able to write to drive c without any problem. What is the cause? Could files in ISO image be corrupted?
 
Take care,
Bryan

---

### Post by mika0110 on 2010-11-21
if the error message appears, click ignore(4,5 time).I also tried and succeeded.
Have fun.

---

### Post by bcbc on 2010-11-22
Copy the wubi.exe from the CD to a folder on your computer. Then copy in that .iso you downloaded to the same folder. Then run wubi.exe from there.

Make sure you run as administrator and have internet access.

If that doesn't work post the log file from the %temp% directory between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

---

