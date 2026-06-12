---
title: "Getting stuck at GRUB is loading , welcome to GRUB"
date: 2023-11-05
forum: Installation &amp; Upgrades
---

### Post by anas559 on 2023-11-05
Hello,
I have hp dv6 latop that only support Bios boot mode (non UEFI)
I tried to burn Ubuntu 22.04.3 LTS to usb flash drive using rufus and then tried to boot it, I get stuck at GRUB is loading , welcome to GRUB.
I tried to use another usb drive and other image burner instead of rufus,the same problem appears.
I tried to use older versions of ubuntu without any issue. The problem only appears at the new version.

Did ubuntu stop supporting Bios mode in this new version?

---

### Post by Rubi1200 on 2023-11-05
Did you try using dd mode in Rufus to write the image?

What happens when you try booting now?

---

### Post by anas559 on 2023-11-05
> **Rubi1200 said:**
> Did you try using dd mode in Rufus to write the image?

What happens when you try booting now?

Thank you for answering me,
I always use ISO mode.
 I tried to use DD mode a moment ago, when I boot I  get stuck at black screen with word GRUB and nothing happens.
 This  problem only occur at this new version only. I don't face any issue with older versions of Ubuntu. There is something wrong with this new version.

---

### Post by MAFoElffen on 2023-11-05
You are talking about 22.04.3 right?

That ISO image seems to work with a lot of computers... You are in good hands with Rubi1200.

You have verfied that it was a good download right? From Windows, select the <Windows> key, type "PowerShell" <Enter>. At the PowerShell prompt, type "Get-FileHash" <space> key, then drag the file from the file explorer onto that Powershell window, and it will finish filling out the path to, and filename to it. <Enter> key.

It should match up with this:
```

a435f6f393dda581172490eda9f683c32e495158a780b5a1de422ee77d98e909 *ubuntu-22.04.3-desktop-amd64.iso

```

---

### Post by anas559 on 2023-11-05
> **MAFoElffen said:**
> You are talking about 22.04.3 right?

That ISO image seems to work with a lot of computers... You are in good hands with Rubi1200.

You have verfied that it was a good download right? From Windows, select the <Windows> key, type "PowerShell" <Enter>. At the PowerShell prompt, type "Get-FileHash" <space> key, then drag the file from the file explorer onto that Powershell window, and it will finish filling out the path to, and filename to it. <Enter> key.

It should match up with this:
```

a435f6f393dda581172490eda9f683c32e495158a780b5a1de422ee77d98e909 *ubuntu-22.04.3-desktop-amd64.iso

```

Yes. it matches exactly.

How can I manage to boot normally like other older versions of Ubuntu?

---

### Post by Rubi1200 on 2023-11-05
What do you have installed on the laptop now?

Have you double checked in BIOS to make sure the boot order is set correctly to use the USB with the new version?

Do you by chance have another USB with a previous version of Ubuntu that will boot into the live environment?

If yes, please run the boot info script in my signature. Paste the link to the results back here for review. No need to repair, just the results please.

---

### Post by MAFoElffen on 2023-11-05
That laptop was Radeon HD 5470 graphics... When that came out in 2010, you had to install the drivers. In later kernels the GPU driver is in the kernel. But now AMD has both Radeon and amdgu...

I'm wondering if they are getting confused(?)

Do you get to a Grub2 menu? If you do... what happens if you add these to the end of the Linux Boot line after "quiet splash"?
```

radeon.si_support=1 amdgpu.si_support=0 radeon.cik_support=1 amdgpu.cik_support=0

```

---

### Post by anas559 on 2023-11-06
> **Rubi1200 said:**
> What do you have installed on the laptop now?

Have you double checked in BIOS to make sure the boot order is set correctly to use the USB with the new version?

Do you by chance have another USB with a previous version of Ubuntu that will boot into the live environment?

If yes, please run the boot info script in my signature. Paste the link to the results back here for review. No need to repair, just the results please.

I have windows 11 installed on the laptop but it is very slow. I already checked the boot order to boot from the usb.
I used older version of ubuntu 20 to boot and then got this report for you to check.

[https://termbin.com/5fvbv](https://termbin.com/5fvbv)

---

### Post by anas559 on 2023-11-06
> **MAFoElffen said:**
> That laptop was Radeon HD 5470 graphics... When that came out in 2010, you had to install the drivers. In later kernels the GPU driver is in the kernel. But now AMD has both Radeon and amdgu...

I'm wondering if they are getting confused(?)

Do you get to a Grub2 menu? If you do... what happens if you add these to the end of the Linux Boot line after "quiet splash"?
```

radeon.si_support=1 amdgpu.si_support=0 radeon.cik_support=1 amdgpu.cik_support=0

```

No my laptop has Radeon 6730m HD graphics. I am not able to reach the grub menu when booting the new version of ubuntu from the usb drive for the first time.

---

### Post by MAFoElffen on 2023-11-06
Hmmm... 20.04 boots fine. the AMD Radeon, at least with 20.04 is using the opensource radeon driver...

You did not answer if the 22.04 LiveUSB gets to a Grub2 menu...

---

### Post by anas559 on 2023-11-06
> **MAFoElffen said:**
> Hmmm... 20.04 boots fine. the AMD Radeon, at least with 20.04 is using the opensource radeon driver...

You did not answer if the 22.04 LiveUSB gets to a Grub2 menu...

No, I get stuck with black screen Grub is loading, Welcome to Grub.

---

### Post by MAFoElffen on 2023-11-06
In that case, just install as 20.04 > update it to latest updates > then do
```

sudo do-release-upgrade

```
...to move it on to 22.04. That will work. And take less time than figuring out the other why's.

Sometimes it's just easier to 'go with the flow' of what "is" working for you, and your machine.

You could spend days to weeks trying to figure out the "why" it is not, or just have a working system that is at your goal, and go on. I think you need to let go, and get a win on your side. Right?

*** Just as another idea to throw in here... If you are doing a new fresh install, and nothing else is going to be there (Erase All and install) now would be a great time to add a new fresh GPT partition table and install it onto that. ("Try" > GParted > Devices > Add new partition table > GPT > Apply...) That is a 13 year old laptop. Using GPT will get it over that "4 primary partition limit", and open so much more to you, if your ever have to move to newer hardware later. You never know, and doing that now would be the time to think about the future.

---

