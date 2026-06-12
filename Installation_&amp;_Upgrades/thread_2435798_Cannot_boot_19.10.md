---
title: "Cannot boot 19.10"
date: 2020-01-26
forum: Installation &amp; Upgrades
---

### Post by francktheminer on 2020-01-26
Hey,
I'm running a Asus ROG b450f Gaming paired with a ryzen 5 3600x and an MSI RX 5700XT Evoke OC, with 16gb of RAM and I tried installing 19.10, which gave me a few ACPI errors, showed in the picture I attached... I honestly have very little clue as to why this might happen, as I've installed Ubuntu on multiple other machines but this never happened, however they were always Intel machines so that might be somewhat related, but that's all speculation...
All help is thanked

---

### Post by P-I H on 2020-01-26
I have about the same hardware components and I also get the same acpi error, but that don't impact boot or functionality. There are some reports about the problem. It might be some bios problem.
A search with " asus b450 AE_AML_UNINITIALIZED_ELEMENT" give some hits. My system works and boots OK both on Ubuntu 19.10 and 20.04. In case you have problems to install or boot Ubuntu there is probably another problem.
I use an UEFI only system.
I have made some changes to get sensors and suspend working. This and my hardware components are available on this link
[https://ubuntuforums.org/showthread.php?t=361236&page=94](https://ubuntuforums.org/showthread.php?t=361236&page=94)

I have also updated BIOS to 2704.

---

### Post by francktheminer on 2020-01-26
Huh, probably BIOS issues... I'm on 3003 cuz I have two m.2 drives and prior versions crashed... Well that sucks, idk what to do now :/

---

### Post by P-I H on 2020-01-26
I have also 2 NVme disks, that performs according to specifications, as you could see in my hardware specification.
- Kingston model: SA1000M8480G as /dev/nvme0n1
- Samsung model: SSD 960 EVO 250GB as /dev/nvme1n1
What happens at boot?
The big difference is that I have a first gen Zen CPU.
Have you tried to install the development version Ubuntu 20.04.

---

### Post by francktheminer on 2020-01-27
Yeah my mobo crashes with the 2 nvmes with gen 3 Ryzens... Gonna try 20.04, edit if it works

---

### Post by oldfred on 2020-01-27
have you also updated firmware on the SSDs?

---

### Post by francktheminer on 2020-01-27
I didn't know you could update SSDs... But at least it's up and running now on 20.04

---

### Post by oldfred on 2020-01-27
I just updated my Samsung. It has a bootable ISO, but looked like an old DOS screen when booted. 
 Last field is version - FW Rev.

```
fred@fred-Z170N-focal:~$ sudo nvme -list
[sudo] password for fred: 
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     S4P2NF0M514514L      Samsung SSD 970 EVO Plus 500GB           1         133.30  GB / 500.11  GB    512   B +  0 B   2B2QEXM7

```

---

