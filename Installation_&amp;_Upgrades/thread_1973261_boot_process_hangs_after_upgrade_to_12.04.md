---
title: "boot process hangs after upgrade to 12.04"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by rodotheos on 2012-05-04
Hi guys,
I had the 11.10 version and decided to upgrade it to the 12.04 one. The upgrade was done without any problems but when I reboot the machine, the process hangs after * Checking battery state...  


In case it helps...
Grub: Ubuntu, with Linux 3.0.0-17-generic

Thank you in advance,
Theo.

---

### Post by gordintoronto on 2012-05-04
There are a million possible reasons, but the most common one relates to the video adapter (which one?) and the most common solution is to use "nomodeset". You can Google details about how to specify nomodeset in Ubuntu 12.04.

---

### Post by rodotheos on 2012-05-07
I tried nomodset but with no luck.
To be honest I hardly understood what it's about.

Is there any other way to login into my account and copy all my files to an external hard disk? I have so many files there concerning my job and I cannot access them.

Please, I'll really appreciate any help.


img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by cyril.godart on 2012-05-07
Hi there,
I had the same issue. I solved it by burning boot-repair on a CD/DVD:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
After booting in to the Boot-repair system (nicely done) I just chose the default 
fix. It worked for me. 

Best

---

