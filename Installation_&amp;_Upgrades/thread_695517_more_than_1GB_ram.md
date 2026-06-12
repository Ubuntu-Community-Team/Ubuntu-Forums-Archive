---
title: "more than 1GB ram"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by russomiche on 2008-02-13
Hello,

My laptop has 2GB of ram but:

russomiche@topolino:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        994         16          0         53        583
-/+ buffers/cache:        357        653
Swap:          956         33        923

That is, my system recognizes only 1GB... please, could you help me?

Regards,

Michele

---

### Post by Pumalite on 2008-02-13
Could you please copy+paste the output here?

---

### Post by russomiche on 2008-02-13
Here is the ouput:

[FONT="Fixedsys"]russomiche@topolino:~$ free -m
total used free shared buffers cached
Mem: 1011 994 16 0 53 583
-/+ buffers/cache: 357 653
Swap: 956 33 923[/FONT]

---

### Post by R13120(1&lt; on 2008-02-13
i'd make sure both of your sticks are plugged and check what the bios reads on your ram.

---

### Post by russomiche on 2008-02-13
Yes, bios reports 2GB and also my previous linux installation (gentoo) correctly saw 2GB of ram.

---

### Post by Pumalite on 2008-02-13
Do memtest: [http://www.memtest86.com/download.html](http://www.memtest86.com/download.html)
Let it run for 8 to 12 HRS.

---

### Post by kellemes on 2008-02-13
> **Pumalite said:**
> Do memtest: [http://www.memtest86.com/download.html](http://www.memtest86.com/download.html)
Let it run for 8 to 12 HRS.

Wow, really that long?

---

### Post by russomiche on 2008-02-13
> **Pumalite said:**
> Do memtest: [http://www.memtest86.com/download.html](http://www.memtest86.com/download.html)
Let it run for 8 to 12 HRS.


No I'm sure it is not an hw problem! If I switch to WinXP it reports 2GB of physical ram. 

Any other idea?

---

### Post by 5-HT on 2008-02-13
Are you running a custom kernel? Did you set CONFIG_HIGHMEM4G=y?
Looks like HIGHMEM support is not enabled and you're using a 3G/1G split leaving only 1G of physical memory being mapped.

The default ubuntu kernels do have HIGHMEM4G support though, so if you're running one it's something else entirely. 
In that case, what happens when you explicitly stipulate 2G of physical memory as a boot option (mem= in megabytes)?
cheers,

---

### Post by russomiche on 2008-02-13
> **5-HT said:**
> Are you running a custom kernel? Did you set CONFIG_HIGHMEM4G=y?
Looks like HIGHMEM support is not enabled and you're using a 3G/1G split leaving only 1G of physical memory being mapped.

The default ubuntu kernels do have HIGHMEM4G support though, so if you're running one it's something else entirely. 
In that case, what happens when you explicitly stipulate 2G of physical memory as a boot option (mem= in megabytes)?
cheers,

Thanks for your kindly reply. No, I don't use a custom kernel.

Sorry but I am a newby so, please, could you let me know how set boot option?

Thanks in advance,

Michele

---

### Post by Pumalite on 2008-02-13
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

