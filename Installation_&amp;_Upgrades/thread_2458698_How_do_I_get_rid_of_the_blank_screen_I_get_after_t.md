---
title: "How do I get rid of the blank screen I get after trying to boot Ubuntu 18.04.4 LTS?"
date: 2021-03-02
forum: Installation &amp; Upgrades
---

### Post by goahead97 on 2021-03-02
Hello

I have an Acer Aspire 515-55 with UEFI bios and I get a blank screen after trying to boot with the desktop version of 64 bits Ubuntu 18.04.4 LTS image of a USB stick. I downloaded this ISO image from [http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/)

I need to install Ubuntu 18.04.4 LTS because I need to use a hardware-software and the manufacturer of this mentioned explicitly Ubuntu 18.04.4 LTS as compatible operating system but did not mention anything about more modern versions of Ubuntu.

Some tests I remember that I have already done:
- I have tried to boot with the same USB stick with an image of the 64 bits Ubuntu 20.04.2.0 LTS and this one works as expected.
- I have tried to boot with the same USB stick with 64 bits LXLE Ubuntu 18.04.3 and I get the same blank screen after selecting the install or the try live option.
- I have also tried with 32 bits LXLE Ubuntu 18.04.3 and I get the same blank screen. Nonetheless taking this USB stick to an old 32 bits computer worked alright. This leads me to think the problem might have something to do with UEFI.
- I have tried to create all these images with several apps such as: unebootin, mkusb, rufus and may be others I do not remember now.
- I have tried replacing quiet splash with nomodeset by typing e on the menu before selecting the install option.
- I have disabled the bios secure boot
- I have replaced the Optane without RAID with AHCI
- I have tried to replaced UEFI with Legacy but UEFI is greyed out in my bios, regardless of whether there is a supervisor or user password set or not.

The only thing I can think of now that I must still try is typying ctrl+c when I see the option to install Ubuntu in order to go to the Grub2 command prompt and once there trying to boot Ubuntu iso image of the USB drive. I do not know though how to boot Ubuntu from the GRUB2 command prompt.

If anyone knows or has any idea to approach this issue, I would appreciate any idea.

I already posted this question on [https://askubuntu.com/questions/1319860/how-do-i-get-rid-of-blank-screen-with-fixed-cursor-to-install-ubuntu-from-usb-dr](https://askubuntu.com/questions/1319860/how-do-i-get-rid-of-blank-screen-with-fixed-cursor-to-install-ubuntu-from-usb-dr) but that did not help me much so far. I hope I did not break any forum rule posting a question about the same issue in this forum. I just did so because I need to be able to install Ubuntu 18.04.4 LTS asap for work reasons.

Thanks

---

### Post by tea for one on 2021-03-02
Was your PC recently released? (i.e. you may need to use Ubuntu 20.04 to support  new hardware)
> I need to install Ubuntu 18.04.4 LTS because I need to use a hardware-software and the manufacturer of this mentioned explicitly Ubuntu 18.04.4 LTS as compatible operating system but did not mention anything about more modern versions of Ubuntu.

Please give details of this hardware-software?

---

### Post by goahead97 on 2021-03-02
This might be the case but I already installed LXLE 64 bits Ubuntu 18.04.3 once in this computer by means of this USB stick. Actually I am using right now this Ubuntu 18.04 but a bit updated upto 18.04.5 to be able to cope with WIFI drivers compatibility. I only formated the USB stick again to move the new image Ubuntu 18.04.4 LTS to the USB stick and since then all the images, including ubuntu 18.04.3 64 bits LXLE that I moved back again to the same USB stick had the same problem.

That is why I do not know why I cannot boot up Ubuntu 18.04 again from a USB stick as I already did once.

Anyway my computer is an Acer Aspire 515-55-54SZ.

Processor    Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz, 1190 Mhz
8 GB RAM

---

### Post by deadflowr on 2021-03-02
18.04.2 to 18.04.5 all use the same hardware stack.
So if you need 18.04.4's hardware stack just install the current 18.04.5.

---

### Post by grahammechanical on 2021-03-02
You could try Ubuntu 18.04.5 instead

[https://releases.ubuntu.com/18.04/](https://releases.ubuntu.com/18.04/)

Last year a serious vulnerability in the Grub2 bootloader was detected. It was called boothole. With a lot of cooperation between Linux distributors and Microsoft a solution was found. It meant patching Grub2. But Grub in existing ISO images could not be retro-actively patched. This meant that using and installing from these older ISO images would potentially compromise the security of the installation.

The solution was for Microsoft to update its secure boot database on all the machines running Windows to revoke the secure boot certificates of these ISO images.

This could explain why 18.04.4 does not boot but 20.04 does boot. And 18.04.5 might boot. You can read all about it here.

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

What makes you think that your desired application would not run successfully on 20.04? What application is it? Imagine that you already had 18.04 installed and was running this particular application successfully. And then you wanted to upgrade to 20.04 because 18.04 was nearing the end of its support life? Would this application stop working? Not necessarily.

Regards

P.S. This forum is governed by different principles to those governing AskUbuntu. We like different people asking the same question. Especially if we already know the answers. We do like them to open their own thread then we can help as individuals.

---

### Post by deadflowr on 2021-03-02
> **deadflowr said:**
> 18.04.2 to 18.04.5 all use the same hardware stack.
So if you need 18.04.4's hardware stack just install the current 18.04.5.

Edit to my previous post, sort of.
18.04.2 and newer uses a rolling hardware stack, which is updated each point release to a version related to the releases in between the LTS releases.
(18.04.2 used the stack used by 18.10
18.04.3 used the stack used by 19.04
18.04.4 used the stack used by 19.10
and 18.04.5+ uses the stack used by 20.04)

Only the original stack used in 18.04( and 18.04.1) and 18.04.5 are supported anymore.

---

### Post by Impavidus on 2021-03-02
> **goahead97 said:**
> 
I need to install Ubuntu 18.04.4 LTS because I need to use a hardware-software and the manufacturer of this mentioned explicitly Ubuntu 18.04.4 LTS as compatible operating system but did not mention anything about more modern versions of Ubuntu.

If the manufacturer didn't explicitly state that 20.04 doesn't work, then chances are that the manufacturer simply forgot to update instructions after 20.04 was released. And if you install 18.04.4 and install all available updates, you'll get to exactly the same system as if you installed 18.04.5 and installed all available updates. And as you always should install those updates, installing 18.04.4 doesn't make sense.

---

### Post by goahead97 on 2021-03-02
I just found out something strange:

I changed back to secure boot in my bios settings to see what happens. And then I realized that with these settings:

1- I cannot boot up with my external SSD's Ubuntu 18.04.5. This is the SSD I installed from 64 bits LXLE 18.04.3 and got updated afterwards into 18.04.5 by me. I get the screen displayed in attachment for this case. I must say though, this SSD's Ubuntu 18.04.5 boots successflly when secure boot is disabled in the bios.

[ATTACH=CONFIG]288044[/ATTACH]
2- I cannot boot up with a USB stick with the Ubuntu 18.04.4 image that I got from [http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/)
3- I can boot up with a USB stick with LXLE 64 bits Ubuntu 18.04.3
4- I can boot up with  internal SSD's Windows 10

---

### Post by goahead97 on 2021-03-02
The reason why I want to install Ubuntu 18.04.4 LTS is that I need to use Vitis, Alveo U280 and Alveo U50 and according to the information of the manufacturer's website with reference to installation requirements for Vitis and for the datacenter accelerator card Alveo U280, I thought Ubuntu 18.04.4 LTS might be the best choice:

For Vitis 2020.2 they mentioned Ubuntu 18.04.4 LTS among other versions.

[https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/acceleration_installation.html#vhc1571429852245](https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/acceleration_installation.html#vhc1571429852245)



For Alveo U280 they only mentioned 2 versions of Ubuntu: Ubuntu 16.04 and Ubuntu 18.04 on this link.
[https://www.xilinx.com/products/boards-and-kits/alveo/u280.html#gettingStarted](https://www.xilinx.com/products/boards-and-kits/alveo/u280.html#gettingStarted)

[LIST]
[*][COLOR=#7B7A7A][Vitis Application Acceleration Development Flow Documentation]("https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/kme1569523964461.html")[/COLOR]
[LIST]
[*][COLOR=#7B7A7A][Getting Started with Vitis]("https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/zeq1569273658063.html")[/COLOR]
[LIST]
[*][COLOR=#7B7A7A][Vitis Software Platform Release Notes]("https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/acceleration_release_notes.html#wlk1553469789555")[/COLOR]
[*][COLOR=#7B7A7A][Installation]("https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/acceleration_installation.html#vhc1571429852245")[/COLOR]
[/LIST]
[/LIST]
[/LIST]
[COLOR=#7B7A7A]
[/COLOR]I thought using Ubuntu 18.04.4 LTS would make sure my operating system meets their required operating system and that is not the cause of any problem I might find while using both Vitis, Alveo U280 and Alveo U50.[COLOR=#7B7A7A]
[/COLOR]

---

### Post by goahead97 on 2021-03-03
Solution that eventually worked for me:


1. Enable secure boot in the bios settings. This was the key at least for me. With secure boot disabled I got a blank screen.


2. Boot from USB stick that has the desktop image of Ubuntu mentioned in my first message ([http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/))


2. Before typing the enter key to proceed with Ubuntu install, type e. Then replace "quiet splash" with "nomodeset"


3. Type F10 to boot from there.

---

### Post by CelticWarrior on 2021-03-03
Nomodeset isn't a solution, just a temporary workaround.

And [your very own link]("https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/acceleration_installation.html#vhc1571429852245") clearly mentions 20.04. Why not use that? It seems that you misread and/or are misinterpreting a lot here.
The minimal requirements are about a minimal kernel version, not a specific kernel version. It makes no sense to insist in using 18.04.4 when there's a newer point release. And, again, 20.04 CAN be used. The 18.04.4 that you install now will be upgrade to 18.04.5 in a couple of minutes just by installing the proposed updates therefore installing specifically 18.04.4 is a complete nonsense.

Now, circling back to the beginning, "nomodeset" (+ Secure Boot) prevents loading proprietary drivers for graphics among other things that can very well include the hardware you want to run. So, it's another nonsense that you think is a solution but it really isn't. **The solution should be the opposite, i.e., disable Secure Boot, NOT use "nomodeset", install the latest LTS, 20.04**.

---

