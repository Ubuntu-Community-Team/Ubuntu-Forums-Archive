---
title: "Loading CD stuck at initramfs"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by NikUk on 2008-03-05
Hi there. Never used Linux before, figured I'd try it and see tonight. Having a bit of a tough time of loading from the CD and was hoping someone may be able to give me a few pointers. 

I want to be able to dual boot Vista and Linux. I have downloaded and burned a CD from the latest Linux Ubuntu download. 

My PC is: System Information
------------------
Time of this report: 3/5/2008, 22:15:28
       Machine name: NIK-PC
   Operating System: Windows Vista™ Home Premium (6.0, Build 6000) (6000.vista_gdr.071023-1545)
           Language: English (Regional Setting: English)
System Manufacturer: NVIDIA
       System Model: C51MCP55
               BIOS: )Phoenix - Award WorkstationBIOS v6.00PG
          Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (2 CPUs), ~2.4GHz
             Memory: 2046MB RAM
          Page File: 1200MB used, 3824MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6000.16386 32bit Unicode

Ok. So anyway. I boot from the CD, and initially i get stuck with a Kernel Panic - not syncing 10-Apic timer doesnt work. Googled that and found that by adding "noapic" in the command line at boot up, I can now get passed this. 

So now I go to the Ubuntu loading screen. After a few seconds it goes to the Initramfs prompt. Keyboard doesnt work here by the way. Not sure if that is important?

After another minute I then get the following message:

"(initramfs) [    47.268000 sd 7:0:0:0: [sdb] Assuming drive cache : write through [    47.272000] sd 7:0:0:0: [sdb] Assuming drive cache : write through"

Then after maybe ten minutes or so, the screen faded to black and stayed like that. I know its not the CD as I had it up and running on a laptop no problems. I tried googling the numbers in the message but the only thing I came up with was someones problem with a webcam?

I'd really like to give linux a good spin and get to know it, but it is really frustrating for a long time windows user to be stuck before passing the starting line. At least I suppose as a Windows user, I am used to this sort of annoyance and I have learnt patience! ;)

If anyone has any non technical info that could help me out, I would be most grateful. Failing that technical jargon will just have to do and I will try very hard to decipher it!

Many thanks in advance!

Nik

---

### Post by NikUk on 2008-03-06
Anyone have any ideas? Help! ? :)

---

### Post by NikUk on 2008-03-06
little bump....

---

### Post by NikUk on 2008-03-06
Go figure. Make me feel really daft. So I finally figure out I downloaded the one "not" for AMD64. hmmmm.... maybe installing Linux is not a good idea for someone as dumb as me. Well I'll try with the correct version and keep my fingers crossed I dont blow up my machine! :)

---

