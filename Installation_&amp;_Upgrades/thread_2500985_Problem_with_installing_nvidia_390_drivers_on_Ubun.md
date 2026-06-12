---
title: "Problem with installing nvidia 390 drivers on Ubuntu 24.04 LTS"
date: 2024-09-18
forum: Installation &amp; Upgrades
---

### Post by em-ix on 2024-09-18
Hello,

I have old desktop PC build on B75A-G43 (MS-7758) v.2.0      motherboard ([https://cz.msi.com/Motherboard/B75AG43/Specification](https://cz.msi.com/Motherboard/B75AG43/Specification))      and as GPU I am using GeForce GTS 450 rev a1 which required nvidia-390 drivers      ([https://www.nvidia.com/en-us/geforce/drivers/results/137276/](https://www.nvidia.com/en-us/geforce/drivers/results/137276/)).

    Recently I upgraded to 24.04.1 LTS (kernel is 6.8.0-45-generic) and now I have problem with      installing nvidia-390 drivers. 

Could someone help me with it?
    
What I did:

    ```

sudo apt upgrade
sudo apt autoremove

sudo add-apt-repository --list|grep URI
  URIs:      [https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/)
  URIs:      [https://ppa.launchpadcontent.net/kelebek333/nvidia-legacy/ubuntu/](https://ppa.launchpadcontent.net/kelebek333/nvidia-legacy/ubuntu/)
sudo add-apt-repository --remove [ppa:graphics-drivers/ubuntu/](ppa:graphics-drivers/ubuntu/)
sudo add-apt-repository --remove [ppa:kelebek333/nvidia-legacy](ppa:kelebek333/nvidia-legacy)

sudo apt purge *nvidia*
sudo apt update

sudo add-apt-repository [ppa:kelebek333/nvidia-legacy](ppa:kelebek333/nvidia-legacy) # --> [https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)
sudo apt update
sudo add-apt-repository --list|grep URI
  URIs:      [https://ppa.launchpadcontent.net/kelebek333/nvidia-legacy/ubuntu/](https://ppa.launchpadcontent.net/kelebek333/nvidia-legacy/ubuntu/)
    
sudo apt search 390
sudo apt install nvidia-driver-390
reboot

```

After reboot result was blank screen with blinking cursor.

 dmesg: [https://pastebin.com/cWUcxT8S](https://pastebin.com/cWUcxT8S)

In the console I have to sudo apt purge *nvidia* and reboot.

Thank you.

---

### Post by Bashing-om on 2024-09-18
m-ix; Ouch

I be that harbinger of ill news.
Nvidia 390 is now retired and is no longer supported.
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

In 24.04 your only supported recourse with that card is the open source Nouveau driver.
However - there is the PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
390.157-0ubuntu7 that last saw love: Alberto Milone (2023-11-03)
That I would be interested in *IF* this driver is workable.

[INDENT]doubtful, but Maybe ?[/INDENT]

---

### Post by em-ix on 2024-09-19
Thank you for replay.

I tried your suggested PPA ([https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)) and without success.


```

sudo add-apt-repository ppa:graphics-drivers/ppa
add-apt-repository --list|grep URI
  URIs: https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/
sudo apt --purge *nvidia*
sudo apt update
sudo apt search 390
sudo apt install nvidia-driver-390
```

Output from the last command: [https://pastebin.com/m5MfLx8p](https://pastebin.com/m5MfLx8p)
/var/crash/nvidia-kernel-source-390.0.crash: [https://pastebin.com/JNv5DNxN](https://pastebin.com/JNv5DNxN)

But thank you again.

> **Bashing-om said:**
> m-ix; Ouch

I be that harbinger of ill news.
Nvidia 390 is now retired and is no longer supported.
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

In 24.04 your only supported recourse with that card is the open source Nouveau driver.
However - there is the PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
390.157-0ubuntu7 that last saw love: Alberto Milone (2023-11-03)
That I would be interested in *IF* this driver is workable.[INDENT]doubtful, but Maybe ?[/INDENT]


---

### Post by em-ix on 2024-09-19
BTW could someone please recommend me perspective GPU (from future drivers view) to match my motherboard  B75A-G43 (MS-7758) v.2.0 ([https://cz.msi.com/Motherboard/B75AG43/Specification)?](https://cz.msi.com/Motherboard/B75AG43/Specification)?)

Radeon RX580?

Thank you.

---

### Post by Frogs Hair on 2024-09-22
There is a legacy PPA still active , but have no experience using it. I retired and replaced my 730 fermi card. 

[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)

---

### Post by em-ix on 2024-09-24
> **Frogs Hair said:**
> There is a legacy PPA still active , but have no experience using it. I retired and replaced my 730 fermi card. 

[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)

Thank you for the tip, but see my first post. I already tried it.


```

sudo add-apt-repository --remove ppa:graphics-drivers/ubuntu/
sudo add-apt-repository --remove ppa:kelebek333/nvidia-legacy
sudo add-apt-repository ppa:kelebek333/build

sudo apt --purge '*nvidia*'
sudo apt update
sudo apt install nvidia-legacy-390xx-driver

sudo printf "\nGSK_RENDERER=cairo\n">>/etc/environment
reboot

```

Code above - installing 390 nvidia drivers from the kelebek333 build PPA and setting environmental variable GSK_RENDERER to cairo value **SOLVED** my problem with black screen with blinking cursor and empty text items in some applications (calculator for example) BUT does not solve my problem with low fps in urban terror game (10+ fps in 24.04 LTS vs 60+ fps in 22.04 LTS).

So could someone please help me with this low UrT fps issue or help me with any tip for GPU for my motheboard [COLOR=#000000]B75A-G43 (MS-7758) v.2.0[/COLOR]. 

Thank you.

---

### Post by yuricbs on 2024-09-24
Thanks, your instructions worked for me (GT 610 - KUbuntu 24.04.1 LTS). So far I haven't noticed the issues you mentioned (blinking cursor and empty text items).

---

### Post by em-ix on 2024-09-24
> **yuricbs said:**
> Thanks, your instructions worked for me (GT 610 - KUbuntu 24.04.1 LTS). So far I haven't noticed the issues you mentioned (blinking cursor and empty text items).

Glad to see. 
Just one note: Nvidia legacy drivers from Build PPA are intended for testing purposes. See [https://launchpad.net/~kelebek333/+archive/ubuntu/build](https://launchpad.net/~kelebek333/+archive/ubuntu/build) This Build PPA may no longer exist, so in the future use:
```

sudo add-apt-repository --remove ppa:kelebek333/build
sudo add-apt-repository ppa:kelebek333/nvidia-legacy
...

```

---

