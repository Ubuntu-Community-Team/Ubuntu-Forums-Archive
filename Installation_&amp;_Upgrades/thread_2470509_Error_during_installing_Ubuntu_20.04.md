---
title: "Error during installing Ubuntu 20.04"
date: 2022-01-02
forum: Installation &amp; Upgrades
---

### Post by yadnik1 on 2022-01-02
I am trying to dual boot my system. I have changed the boot order to Ubuntu first and am booting currently from pen drive having the image of Ubuntu OS.
However while installing the OS, my system gets stuck on the following step(as shown in image) for hours together. I have configured UEFI setting accordingly as well.
Can someone please help me.
Thank you very much!![IMG]https://ubuntuforums.org/newattachment.php?do=assetmanager&values[f]=333&contenttypeid=1&poststarttime=1641099257&posthash=efcd9b1195f7407ad49a9778863696ce&insertinline=1[/IMG]

---

### Post by guiverc on 2022-01-02
Looks like Ubuntu Desktop 20.04 LTS

You weren't specific as to which update level (20.04? 20.04.1? 20.04.2, 20.04.3 etc) but if it's newer hardware I'd recommend always getting the latest (*and 20.04 or the 2020-April release so it may struggle with hardware that's didn't already exist during it's development*).

At this point I'd switch to a terminal & login.  I usually use Ctrl+Alt+F4 but that's mostly as I find F4 and easy to find without looking.  Login  (*I'd expect username to be "ubuntu**" and password not being required; try just ENTER; I grabbed a random thumb-drive & it was "Ubuntu-MATE" jammy & it didn't ask me for password; but username was "ubuntu-mate"*)

I'd firstly look for squashfs errors, something like\

```
sudo dmesg |grep squash
```

should provide only a message showing version number, developers name etc. I may appear more than once, but what I'd primarily look for is lines that say "**squashfs**" as those are errors & trouble with your installation media (*trouble trying to read it*).

I'd also quickly to check the media check completed succesfully, ie. 

```
journalctl |grep 'Check finished'
```

where you'd expect a line something like

date time ubuntu casper-md5check[number]: Check finished: no errors found.

If a line like this is found; your media is good and scan of installation media completed successfully.  

 This is what I'd check first  (but I'm mostly doing QA or *Quality Assurance*) thus hardware issues are not usually my concern, thumb-drives are cheap consumable media & this mostly checks for that **weak**point in the testing process.

You also mention configuring UEFI which has me confused; no changes to that should be required if the ISO was written to your installation media correctly (*but all hardware/firmware is somewhat unique, so general rules rarely help!*).

Details of the box you're installing to may help, if it turns out your installation media is perfect (ie. "Check finished: no errors found") and what you changed, or felt you needed to change in your uEFI setup.

---

### Post by yancek on 2022-01-02
You indicate you are trying to dual boot but not what you are trying to dual boot?  windows 10?  windows 11? some other version or OS?

THe image you posted shows that you have selected to download updates during the install, do you have your internet configured/set up before doing this?  If you are trying to dual boot with windows 10, the link below is the official documentation on that process.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yadnik1 on 2022-01-02
Thanks,

Will surely check it out.

However my laptop is buffering on that step itself since last 8 hours. I tried the commands as I was told by guiverc, however they did not return any message or info.
I am trying to dual boot with windows 10 (The os already exists in my laptop and now am trying to install Ubuntu by partitioning my HDD).
Windows exists in SSD and I am partitioning my HDD for installing Ubuntu.
Yes I have connected to Wifi while installing Ubuntu.

Thank you very much!!

---

