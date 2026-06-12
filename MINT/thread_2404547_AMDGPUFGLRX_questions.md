---
title: "AMDGPU/FGLRX questions"
date: 2018-10-25
forum: MINT
---

### Post by rdlf0512 on 2018-10-25
OK so first, a little warning for those of you who are planning on buying an AMD-based laptop.
Mine is an Acer Aspire 5 with AMD A12-9720P with RX540 GPU. Admittedly I confess I should have done my research before buying this machine.
To start, for some reason, AMD does not even MENTION their own processor on their website. AMD A12 9700 is there, and so is the 9730P, but 9720P is lacking: attachment (amdissue01.png)
[https://imgur.com/a/tgX175](https://imgur.com/a/tgX175)
I'm kinda forced to go with 9700P (because it isn't a 9730P) and it gets even worse: there is no driver for Linux users, only Windows: attachment (amdissue_02.png)
[https://imgur.com/a/YJ9HSZC](https://imgur.com/a/YJ9HSZC)

After sending a few emails to AMD's tech support team, that's what I got:
> 
Thank you for the response.

Yes, I understand the concern here, but we do not have exact information when there will be supported drivers released for A12-9720P APU or RX 540 graphic card.

I request you to subscribe to the newsletter so that you can receive latest updates on the new product releases.

[http://www.amd.com/en-us/who-we-are/subscriptions/announcements](http://www.amd.com/en-us/who-we-are/subscriptions/announcements)

Thank you for contacting AMD.

After sending my information in order to subscribe to AMD's mailing list, I get a 404 Page not found error.

So I concluded official help is out of question when it comes to supporting the A12-9720P and RX540.
With that, I looked up AMDGPU to see whether it does what AMD doesn't do: support my APU/GPU on Linux.
(FYI, I also tested Don't Starve on Steam. Frame-wise, it does a great job. However, I see screen tearing all over the place. It gets sooo annoying over time.)
Before making a move on and try the AMDGPU driver, I'd like to know what driver I'm using currently. This is a Linux Mint 19 (which is based on Ubuntu 18.04) laptop.

If you use this APU (For LAPTOP, that is), please let me know: is it worth installing it? Have you seen any benefit on doing that on your games?
Because official support is out of question, there is no FGLRX available. So AMDGPU is the only way to go. This [very old Ubuntu Forums post #2]("https://ubuntuforums.org/showthread.php?t=2317751") suggests doing a 
> 
sudo apt-get install xserver-xorg-video-amdgpu libdrm-amdgpu1

But that was almost two years ago. Is there more to it than just that nowadays?
Will it get rid of screen tearing when playing a game or when scrolling up and down?

Please let me know.

Thanks.

---

### Post by gdesilva on 2018-10-25
As you quite correctly mentioned there is no fglrx support anymore and system loads the radeon or appropriate opensource driver. Your images show that there is no proprietary APU driver for Linux - the only available for Windows - so, I am not sure of your intentions to install a APU driver in the first place??? Perhaps, I am missing something here?

---

### Post by QIII on 2018-10-25
Before we go off half-cocked and follow old instructions, would you please post the results of 

```
lsmod | grep amdgpu
```

and 

```
lsmod | grep radeon
```

so we can see which driver module is loaded?

---

### Post by rdlf0512 on 2018-10-25
> **gdesilva said:**
> As you quite correctly mentioned there is no fglrx support anymore and system loads the radeon or appropriate opensource driver. Your images show that there is no proprietary APU driver for Linux - the only available for Windows - so, I am not sure of your intentions to install a APU driver in the first place??? Perhaps, I am missing something here?
Yes, my intention is to install the driver. Actually, since we're going the technical route, my real intentions are:
To install or to make sure my APU firmware protects it from Meltdown or Spectre;
To install the APU controller/switcher. As you know the chip houses the CPU, iGPU (for non-intensive tasks) and my GPU (RX540, 2GB GDDR5 memory).
I know this might be something that only the driver itself can do. But I wonder whether AMDGPU can handle it or not. According to [this page]("https://help.ubuntu.com/community/AMDGPU-Driver"), it does support Carrizo APUs, which mine is based on. Problem is, I believe the website was mention desktop APUs, not laptop ones. But it shouldn't matter really, because they both use the same architecture.
> **QIII said:**
> Before we go off half-cocked and follow old instructions, would you please post the results of 

```
lsmod | grep amdgpu
```

and 

```
lsmod | grep radeon
```

so we can see which driver module is loaded?
Sure. Output result for lsmod | grep amdgpu is:
```

amdgpu               2703360  5
chash                  16384  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
ttm                   106496  1 amdgpu
drm_kms_helper        172032  1 amdgpu
drm                   401408  7 drm_kms_helper,amdgpu,ttm

```

And lsmod | grep radeon returns nothing.
So yeah, as it turns out, I was considering to install AMDGPU.. only to realize that I already have it installed. I now know that is a fact, confirmed when I fired up Synaptic and it showed me, there's a checked logo next to xserver-xorg-video-amdgpu.
Playing games like Don't Starve makes all kind of artifacts and screen tearing show up, which to me it means that my graphics chip which is supposed to handle low-tasks is handling it. I need to figure out a way to hand it over to my beefier graphics card. That is why I need AMDGPU. Perhaps it can do it and I just don't know how? Hard to tell, as I have found no GUI or command to do it, but I keep digging...

---

### Post by QIII on 2018-10-25
Because your GPU is supported by AMDGPU, you might try adding the proprietary overlay:  AMDGPU-PRO.  It is dead-easy to install on Ubuntu (it was, in fact, developed on Ubuntu) and just as easy to remove if you decide you don't like it.

Go to AMD's AMDGPU-PRO page to get it.

I'll have to dig through my notes, but there are some items you can change in the config file to make it really sing.

If your dedicated GPU is an AMD, have a look through your BIOS settings to see if you can disable the one on the APU in favor of it.

---

### Post by rdlf0512 on 2018-10-26
OK, so I decided to download the latest amdgpu-pro release (v17.40-492261) and after extracting it and entering the command:
> 
./amdgpu-pro-install -y 

This is all I got:
> 
Unsupported OS


I guess I'm not going anywhere with this.
EDIT: As for the BIOS settings, no, it will not let me choose which GPU I want to go with.
Matter of fact, it's very restrictive. This is an Acer laptop, so I guess that's kinda expected here.

---

### Post by QIII on 2018-10-27
Which release of Ubuntu are you using?

---

### Post by rdlf0512 on 2018-10-27
Linux Mint 19, which is based on Ubuntu 18.04.

---

### Post by jeremy31 on 2018-10-27
Thread moved to Mint
See [https://forums.linuxmint.com/viewtopic.php?t=272074#p1515630](https://forums.linuxmint.com/viewtopic.php?t=272074#p1515630)

---

