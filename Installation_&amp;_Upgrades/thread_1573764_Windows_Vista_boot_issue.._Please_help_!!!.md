---
title: "Windows Vista boot issue.. Please help !!!"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by meghal on 2010-09-13
Hello Friends,
 

 I have Toshiba Satellite A 100 Laptop which was pre-installed with Windows Vista home basic.
 Now, I wanted to try Ubuntu. So I followed the various webpages which guides us through the Dual OS installation and I was happy with the Vista-Ubuntu package.
 Now, I don't know what happened but I screwed up my Ubuntu Partition and just deleted it when using Vista.
 Then when laptop re-started , neither of OS opened. SO I freaked out as I only have one computer to access. I tried re-installing Recovery disc but it didn't help at all. And it kept on saying error 1117 and failed to read image from the source.
 So to use computer, I thought to install Ubuntu on full hard drive. I did that and then I was able to get internet access and work my way through but I do want to re-install Vista.
 From the webpages, I gathered that I might have played with MBR of my laptop. I tried to super grub disk from USB and there I get error 25. I tried to use “sudo apt-install ms-sys” and It says “ms-sys” not found or missing.
 Now at the start I do get GRUB with options of Ubuntu and Windows Vista but whenever I try to boot Vista It says “ winload.exe corrupt or missing”. And the recovery disc of on no use. I have tried it many times.

 Please kindly help.
 I seriously want to re-install vista and I am not going to fiddle with laptop next time, when its not my cup of tea at all !!!
 

 Any help is greatly appreciated.
 

 Thanks,
 Meghal.

---

### Post by viralmeme on 2010-09-13
> **meghal said:**
> I have Toshiba Satellite A 100 Laptop 

Could you post the output of [Gparted]("http://gparted.sourceforge.net/screenshots.php")

---

### Post by meghal on 2010-09-13
> **viralmeme said:**
> Could you post the output of [Gparted]("http://gparted.sourceforge.net/screenshots.php")
I haven't used GParted yet.
Should I use that? How to use that ? Please guide.
Thanks for the reply.

---

### Post by garvinrick4 on 2010-09-13
Try using this with ubuntu Cd. Put cd in tray and boot.
Choose try ubuntu. Open a terminal in Ubuntu. and put these in one at a time.
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
If it says error do not worry we just want the mbr part.

Reboot and should boot into Vista.
If you have a good install of Vista.

---

### Post by viralmeme on 2010-09-13
> **meghal said:**
> I haven't used GParted yet.
Should I use that? How to use that ? Please guide.

Just browse to here and follow the pictures: [Gparted Tutorial]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

---

### Post by meghal on 2010-09-13
> **garvinrick4 said:**
> Try using this with ubuntu Cd. Put cd in tray and boot.
Choose try ubuntu. Open a terminal in Ubuntu. and put these in one at a time.
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
If it says error do not worry we just want the mbr part.
 
Reboot and should boot into Vista.
If you have a good install of Vista.
 
 
Thanks a lot Garvinrick !!!
I am back on Vista.
I highly appreciate it.
 
regards,
Meghal

---

