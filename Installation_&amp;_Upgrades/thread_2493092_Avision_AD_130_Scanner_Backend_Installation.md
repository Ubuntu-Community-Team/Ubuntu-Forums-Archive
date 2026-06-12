---
title: "Avision AD 130 Scanner Backend Installation"
date: 2023-12-03
forum: Installation &amp; Upgrades
---

### Post by SBMN7 on 2023-12-03
Dear Experts, 
I have a scanner device of Avision 130 model and I am trying to configure it in my ubuntu 23.04. But I am not a linux expert user. So, I understand bit slowly about things. I need someone help to configure my scanner device well. Please try to help me.

---

### Post by MAFoElffen on 2023-12-04
Please post the results of this within CODE Tags:
```

sane-find-scanner -vv

```

---

### Post by SBMN7 on 2023-12-04
Dear [MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547"), 
Here is the code of the command you provided.

> gurubhai@gurubhai-81G2:~$ sane-find-scanner -vv
This is sane-find-scanner from sane-backends 1.1.1.463-65779


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
checking /dev/sg0... failed to open (Access to resource has been denied)
checking /dev/sg1... failed to open (Invalid argument)
checking /dev/sg2... failed to open (Invalid argument)
checking /dev/sg3... failed to open (Invalid argument)
checking /dev/sg4... failed to open (Invalid argument)
checking /dev/sg5... failed to open (Invalid argument)
checking /dev/sg6... failed to open (Invalid argument)
checking /dev/sg7... failed to open (Invalid argument)
checking /dev/sg8... failed to open (Invalid argument)
checking /dev/sg9... failed to open (Invalid argument)
checking /dev/sga... failed to open (Invalid argument)
checking /dev/sgb... failed to open (Invalid argument)
checking /dev/sgc... failed to open (Invalid argument)
checking /dev/sgd... failed to open (Invalid argument)
checking /dev/sge... failed to open (Invalid argument)
checking /dev/sgf... failed to open (Invalid argument)
checking /dev/sgg... failed to open (Invalid argument)
checking /dev/sgh... failed to open (Invalid argument)
checking /dev/sgi... failed to open (Invalid argument)
checking /dev/sgj... failed to open (Invalid argument)
checking /dev/sgk... failed to open (Invalid argument)
checking /dev/sgl... failed to open (Invalid argument)
checking /dev/sgm... failed to open (Invalid argument)
checking /dev/sgn... failed to open (Invalid argument)
checking /dev/sgo... failed to open (Invalid argument)
checking /dev/sgp... failed to open (Invalid argument)
checking /dev/sgq... failed to open (Invalid argument)
checking /dev/sgr... failed to open (Invalid argument)
checking /dev/sgs... failed to open (Invalid argument)
checking /dev/sgt... failed to open (Invalid argument)
checking /dev/sgu... failed to open (Invalid argument)
checking /dev/sgv... failed to open (Invalid argument)
checking /dev/sgw... failed to open (Invalid argument)
checking /dev/sgx... failed to open (Invalid argument)
checking /dev/sgy... failed to open (Invalid argument)
checking /dev/sgz... failed to open (Invalid argument)
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
checking /dev/usb/scanner0... failed to open (Invalid argument)
checking /dev/usb/scanner1... failed to open (Invalid argument)
checking /dev/usb/scanner2... failed to open (Invalid argument)
checking /dev/usb/scanner3... failed to open (Invalid argument)
checking /dev/usb/scanner4... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner7... failed to open (Invalid argument)
checking /dev/usb/scanner8... failed to open (Invalid argument)
checking /dev/usb/scanner9... failed to open (Invalid argument)
checking /dev/usb/scanner10... failed to open (Invalid argument)
checking /dev/usb/scanner11... failed to open (Invalid argument)
checking /dev/usb/scanner12... failed to open (Invalid argument)
checking /dev/usb/scanner13... failed to open (Invalid argument)
checking /dev/usb/scanner14... failed to open (Invalid argument)
checking /dev/usb/scanner15... failed to open (Invalid argument)
checking /dev/usbscanner... failed to open (Invalid argument)
checking /dev/usbscanner0... failed to open (Invalid argument)
checking /dev/usbscanner1... failed to open (Invalid argument)
checking /dev/usbscanner2... failed to open (Invalid argument)
checking /dev/usbscanner3... failed to open (Invalid argument)
checking /dev/usbscanner4... failed to open (Invalid argument)
checking /dev/usbscanner5... failed to open (Invalid argument)
checking /dev/usbscanner6... failed to open (Invalid argument)
checking /dev/usbscanner7... failed to open (Invalid argument)
checking /dev/usbscanner8... failed to open (Invalid argument)
checking /dev/usbscanner9... failed to open (Invalid argument)
checking /dev/usbscanner10... failed to open (Invalid argument)
checking /dev/usbscanner11... failed to open (Invalid argument)
checking /dev/usbscanner12... failed to open (Invalid argument)
checking /dev/usbscanner13... failed to open (Invalid argument)
checking /dev/usbscanner14... failed to open (Invalid argument)
checking /dev/usbscanner15... failed to open (Invalid argument)
libusb not available
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
done 

---

### Post by SBMN7 on 2023-12-04
AND when using the isusb command, It detect the scanner, here is it, 
 >  gurubhai@gurubhai-81G2:~$ lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 5986:1127 Acer, Inc EasyCamera
Bus 001 Device 004: ID 0cf3:e500 Qualcomm Atheros Communications 
Bus 001 Device 003: ID 0638:2cfb Avision, Inc. AD130
Bus 001 Device 008: ID 18f8:1286 [Maxxter] USB GAMING MOUSE 
Bus 001 Device 007: ID 413c:2113 Dell Computer Corp. KB216 Wired Keyboard
Bus 001 Device 006: ID 0a05:7211 Unknown Manufacturer hub
Bus 001 Device 002: ID 0a05:7211 Unknown Manufacturer hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gurubhai@gurubhai-81G2:~$ 

---

### Post by MAFoElffen on 2023-12-04
First:
Avision notes that you should power-on and keep holding the power-on button down while both powering on, and during scanning with SANE... 

From how that reads, that may take either two people or a contortionist. LOL

Second:
When posting raw output or commands, please wrap the output or commands with CODE Tags, as I asked. Forum Policy for that is in he Posting guidelines link in my signature line. Instructions for CODE Tags is also in a link in my signature line. Please edit and fix your last post.

---

### Post by SBMN7 on 2023-12-04
Your reply not suppotive. It is just to make feel superior than me. I already said that, I am a beginner. I do not have much knowledge, But I well known about a machine startup process, I did almost things with the help of chat gpt as well. But I am unable to do this stuff. So that I am here for help. But your help really sucks!

---

### Post by MAFoElffen on 2023-12-04
Do not get your feelings hurt over nothing. There were no emotions in my reply at all. Only the facts. I am known to have a lot of patience, and I go out of my way helping people here. I do not need anything from you to validate who I am. Do not blame me for your misunderstanding of that. If you do, I may avoid helping you next time. We do not get paid here. We are all just Users who volunteer our time., and experience to help others. To get self-satisfaction that maybe we can make a difference. If you lighten up, you will find that there is a very good group of people here.

Here is what I did in my last post:
1) I gave you the information from Avision in what they recommend.

2) I gave you a tip to try to keep you out of trouble with the Moderators and Admins here for not following Forum Policy. Possibly to correct the format of what you posted before they noticed...

From the Posting Guidelines, #3:
> 
When posting long outputs from terminal commands or from certain  scripts, or the contents of configuration files, wrap this between[noparse]```
  and 
```[/noparse] tags. This is to preserve essential formatting and to  prevent the posting of large difficult-to-read walls of text.

That tells the staff here that you either didn'y read the posting Guidelines before posting, or you choose to ignore them. Besides what that said, I know that raw output does strange things to the Forums software... If you do not choose to follow the Posting Guidelines, then that is on you personally. That matters nothing to me. That you are willing to help people to be able to help you matters.

You could also edit that post, by selecting "EDIT" > "Advance Edit" to get to the Advanced Editor. Select the text with your mouse to highlight it. Select the "#" Icon from the extended menu of the tool bar to wrap the highlighted text with CODE Tags. Save.

I put those links in my signature line, so that I could refer to them, instead of having to retype it 50 times a day, explaining that... (which you made me do again.)

Good luck with your problem. Good night. I need to move on to other things right now. I will check back later.

---

### Post by ActionParsnip on 2023-12-04
[https://www.hamrick.com/alternate-versions.html](https://www.hamrick.com/alternate-versions.html)
Seems to support the scanner

---

### Post by SBMN7 on 2023-12-05
[ActionParsnip]("https://ubuntuforums.org/member.php?u=1079078"), I already tried Vue Scanner. It is not working with the scanner model I have.

---

### Post by MAFoElffen on 2023-12-05
Thank you for going back and editing your post and adding CODE Tags to it.

In Linux, your Scanner [COLOR=#ff0000]"may be"[/COLOR] supported by SANE, which stands for "Scanner Access Now Easy". It is specially supported by this backend from SANE: [https://manpages.ubuntu.com/manpages/jammy/en/man5/sane-avision.5.html](https://manpages.ubuntu.com/manpages/jammy/en/man5/sane-avision.5.html) . Note that that is provided by package libsane-common, which is a default installed package.

Since you did not provide the information that I asked for in my last post, I will assume either you have that on ignore or feel you can help yourself. 

I will still give you tips and try to lead in in the right direction. Refer to this tutorial:
[https://help.ubuntu.com/community/sane](https://help.ubuntu.com/community/sane)

There are some holes with that tutorial... First off do this:
```

lsusb -vv

```
Find your scanner in that output... Open a text editor, to copy the information from that output into a text document, so your have that info for later. Your Scanner has a USB interface, and cable to your computer, so that is the info you need. Follow the section for USB connected scanners.

Of the packages it say to install, these are what are already installed by default:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt list *sane* --installed
Listing... Done
libsane-common/jammy,jammy,now 1.1.1-5 all [installed,automatic]
libsane-hpaio/jammy,now 3.21.12+dfsg0-1 amd64 [installed,automatic]
libsane1/jammy,now 1.1.1-5 amd64 [installed,automatic]
sane-airscan/jammy,now 0.99.27-1build1 amd64 [installed,automatic]
sane-utils/jammy,now 1.1.1-5 amd64 [installed,automatic]

```
Your scanner does not have a Linux driver available from Avision... They only provide Windows Drivers. Nor do they provide MAC drivers.
The reason I say [COLOR=#ff0000]"may be"[/COLOR]...

Because if I look at this:
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

If you go down to the Avision section to try to look up the devices that SANE says it supports, your model is not in that list...

Elsewhere, not specically for your specific model, I did find where Avision has their own SANE backend driver for their scanners to work with SANE, but I couldn't find that link there, nor could I find any mention of SANE on their site. Where I found the link at Avision, was actually at the SANE GitLab: [https://gitlab.com/sane-project/backends/-/issues/498](https://gitlab.com/sane-project/backends/-/issues/498)

No one actually said what that supported... So what I would do if I were you, would be to contact Avision and ask them yourself.

What I fear... Years ago, I bought a Laser printer that was on sale. Then I found out, that that company didn't ever support their printers working with Linux, nor were they ever planning on it. I hope that you have better luck with this. My hopes for you, is that it looks like many of there scanners do work with SANE, so maybe yours "might." I cannot confirm that. Sorry.

Not even VueScan, who keeps track of many drivers for many scanners, because they want users to knwo that their own software will not conflist with drivers for scanners they might have, does not even list that specific model from Avision(?)

I know my current printer with scanner does work with Linux but I had to play with it for the scanner itself to work with simplescan. Xsane worked better.

---

