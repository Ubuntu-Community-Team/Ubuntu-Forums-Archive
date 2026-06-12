---
title: "problems in the VIRTUALBOX installation"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by fran3 on 2013-08-29
Dear UBUNTUs fans and experts,

I'm new ( 2months ago ) in Linux with **Ubuntu 13.04** , and so far everything had gone very well , slowly learning , but without serious problems .

I say so far, because just yesterday, I instaled **VIRTUALBOX** from ORACLE VM website , in its latest version **4.2.16 for Linux**, and then  the **EXTENSION PACK**, a strange thing happened on my OS : At the first time, the TERMINAL application and the UBUNTU SOFTWARE CENTER aplication disappeared of the computer, and after restarting, the TASKBAR and the UBUNTU PITCHER disappear too, so I could not open anything.

How I mentioned, I am a beginner and didn't know how to find solution to the problem, so I had to reinstall the OS. At first I was trying to reinstall applications recovering but it was reinstalled with the problem again , so in the end I decided to delete the previous OS and install it again, so I was able to have it correctly , but I had lost all the programs that had installed until this time : - S

Today,  just installed the OS , without installing any other application , I installed again VIRTUALBOX  from ORACLE orginal page , then installed the EXTENSION PACK, and voila! The problem happened again, the TERMINAL and SOFTWARE CENTER disappeared again and after to restarted the task bar and launcher disappeared too . So I had to reinstall the OS again .

I wanted to share this to see if anyone had the same probleml or if someone may know it is due .

Thanks you very much and sorry for the english faults.

---

### Post by ibjsb4 on 2013-08-30
Try installing without using the software center.  "dpkg -i"

[https://www.virtualbox.org/manual/ch02.html#idp10779936](https://www.virtualbox.org/manual/ch02.html#idp10779936)

You should also be able to right click on the saved (download) package and use Archive Manager.

Don't forget to install 'dkms' and 'build-essential'

```
sudo apt-get install dkms build-essential
```

---

### Post by fran3 on 2013-08-31
Thanks for your answer,

Finally I could install correctly VirtualBox and set up a virtual machine. I did it installing it through the Softwar Center of Ubuntu, not from the web page and it worked without problems. But I don't know if the problem was because some problem of the setup files, for some problem in my computer or the reason is that I didn't know install correctly.

Anyway, thank you very much!
:-)

---

