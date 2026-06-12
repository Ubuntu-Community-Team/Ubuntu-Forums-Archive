---
title: "Acer Aspire E1-531 - installation and hardrive issues"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Berduchwal on 2013-01-07
I have recently purchased Acer Aspire E1-531 laptop.

It has a new BIOS type which is not very helpful with non Windows operating systems. I needed to change to Legacy Bios and disable secure boot to be able to install Ubuntu at all.

However after few days I started having hard drive issues. After ubuntu book it stopped working after login. After investigation I realised that bios was freezing HDD.

I decided to change BIOS.
I have downloaded BIOS from Acer website. 
BIOS	Acer	1.13	3.8 MB	10/22/2012

Then I installed unetbootin:
```
apt-get install unetbootin
```

Unetbootin had FreeDOS version 1. This is not the latest version but it contains live version and I used it.

I unzipped the file downloaded from acer and change name of the directory to BIOS.

When I booted the laptop from the USB stick with freedos. I went into directory with bios:
```
c:
cd BIOS
q5wv1113.exe
```

Response was:
> Reading file...
Flash package mode.
Options: /bios /b /ecb

Please do not remove the AC power!

Insyde Flash Unitily for insydeH20
Version 1.5w

Initilizing

Current BIOS Model name: Q5WV1
New BIOS Model name: Q5WV1

Current BIOS version: V2.02
New BIOS version: V1.13

Please update to the same type of BIOS (v2.x)

Now I do not really know what to do. Any suggestions?

---

### Post by Pjotr123 on 2013-01-07
Why downgrade your BIOS? I would try the latest first, which is 2.09 (from 2012/12/24). Reasonable chance that this Christmas Eve-edition of the BIOS will solve your HDD problem... If not, it doesn't do any harm.

---

### Post by Berduchwal on 2013-01-07
Thank you for swift reply.

I assumed that since version your mentioned is:

BIOS - **UEFI for Windows 8 (Not for Upgrades)**	Acer	2.09	4.0 MB	12/24/2012

I should update for one without Windows in its name.

However I tried 2.09 and it updated.

Should I also reinstall Ubuntu to work with new BIOS I guess the answer is yes.

Since after new bios keyboard does not work on login screen. It connects to local wifi network ok but then I can do nothing as both keyboard and touch pad are not responsive.

---

### Post by Pjotr123 on 2013-01-07
> **Berduchwal said:**
> 
Should I also reinstall Ubuntu to work with new BIOS I guess the answer is yes.

Since after new bios keyboard does not work on login screen.

Strange. But a new BIOS is a pretty fundamental thing, so I would try a clean reinstall, yes. For example in this fashion:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Make sure to check the BIOS settings for undesirable things first, because the BIOS flash probably put every setting back to default....

---

### Post by Berduchwal on 2013-01-07
Thank you very much for you help again.

I restarted into live and gparted removed all partitions and started clear installation.

It did not even stop once during installation. 
It stopped about 10 times with old BIOS.

So I guess it was a success. Will report if I encounter any issues.

For those considering purchase of this laptop:
1) Webcam, wifi, ethernet card works out of the box no tinkering needed
2) 4GB ram was bit slowish at times so I upgraded to 8gb

---

### Post by Berduchwal on 2013-01-10
[http://support.acer.com/us/en/product/default.aspx?modelId=4097]("http://support.acer.com/us/en/product/default.aspx?modelId=4097")

Sadly updated BIOS to version 2.09 did not help much. All was well for a day and then problems with HDD reappeared.

Since then Acer released another version of BIOS 2.11 issued on 7 January 2013 this made things worst now I could not even install Ubuntu. Hard Drive stopped working and after soft reset you could see HDD frozen in BIOS.

So if you are considering buying this laptop think again.

Acer does not even have a customer support number in the UK only one for repairs. I will give them a week to fix this issue and will return the latop to the seller.

---

### Post by Berduchwal on 2013-01-22
I managed to get in touch with Acer customer support using website below:

[http://www.acer.co.uk/ac/en/GB/content/support]("http://www.acer.co.uk/ac/en/GB/content/support")

Response was long in coming. I posted my question on: 14/01/2013 08.43 PM response was posted on: 22/01/2013 01.35 PM

Advice I got from them is quoted below:

> Regarding your query, I kindly request to reinstall the windows operating system and let me know if the issue still persists.

They also offered to take the laptop for repairs and see if it is a hardware problem.

I am sending the laptop for repairs and will report on progress.

---

### Post by Berduchwal on 2013-02-08
Laptop was returned to me with replaced HDD.

It also has a new 2.13 bios. 

It is hard to say which actually resolved the issue new bios or new hdd.

Previous version of bios is no longer available so I can not test this.

HDD still goes to frozen mode after few minutes of using Ubuntu but this does not make any difference to operation of the machine.

Repair only took them 3 days.

---

