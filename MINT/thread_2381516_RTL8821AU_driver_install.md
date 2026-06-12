---
title: "RTL8821AU driver install"
date: 2018-01-01
forum: MINT
---

### Post by 3dgraphdav on 2018-01-01
I am running linux mint 18.2
dell studio 520
4 gb ram  core 2 quad
I have a new wifi adapter. The adapter did not run out of the package. (computer did not even see it when running the code ifconfig -a)
Run the install.sh that was on the cd that came with it and ran into an error
```
Compile make driver error: 2
Please check error Mesg
```

searching online I found this thread
[https://ubuntuforums.org/showthread.php?t=2339960&page=2&](https://ubuntuforums.org/showthread.php?t=2339960&page=2&)

followed up untill post #11
and wifi now picks up a signal and computer sees that it is there.
it says in post #11 
> You may encounter a few warnings but it should install and work.

Let us know as we will have another step.

I didn't run into any trouble, so just wanted to know if there was anything else that I needed to do.
just making sure to get full used of the adapter (speed, no conflects with other drivers, ect.)
also should I clean up any install files
Thank You

---

### Post by 1-retired-surfer on 2018-01-02
I too have trouble with a new USB style of WiFi adapter. I wonder about the brand of adapter you've got. 

I can use my Alpha unit (a dongle) and it runs very well if I keep Ubuntu busy with some sort of streaming program running all the time - or I get signed-off of the WiFi and cannot get it running again until I reboot. 

Ah well - I'd like to get the other USB WiFi adapter to run. I cannot even 'see' it in my list of adapters and I've installed the CD-ROM Linux drivers that came with the device. 

Next week I'll work on getting my new Wireless Canon Laser printer installed - for which I cannot find a driver anywhere!

---

### Post by howefield on 2018-01-02
Thread moved to the "*MINT*" forum.

---

### Post by 3dgraphdav on 2018-01-23
I ran lipci and this came out
```
Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
```
This is the driver that I have loaded

git clone [https://github.com/diederikdehaas/rtl8812AU.git](https://github.com/diederikdehaas/rtl8812AU.git)

So was wondering, do I have the right driver loaded.. It's working. but just wondering

---

### Post by wildmanne39 on 2018-01-23
If the device is the one in title then it is correct and I am sure it would not work if it was the wrong driver, however the device you posted is your ethernet card please post the output of:
```
lspci -nnk | grep -iA2 net
```
to confirm what I am already sure of.

Thanks

---

