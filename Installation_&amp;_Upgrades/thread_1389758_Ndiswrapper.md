---
title: "Ndiswrapper"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by tacobeans1234 on 2010-01-24
Hello forum,

I'm quite new to the whole "Linux" concept. I just installed Ubuntu using "wubi" and I realized that my PCI network card wasn't supported. I have a Linksys WMP54Gs network card and I already found the .sys and the .inf files that I need. My only problem is installing "Ndiswrapper" to apply said drivers. I downloaded it and I have already moved the .tar.gz file to my ubuntu partition. So my only question is, how do I install it? Also, I don't have any way to access the internet on my ubuntu partition. I'm posting this through the windows side of my HDD. Please go easy on me, It's my first week using Ubuntu.

Thanks for you help! 

--Tacobeans1234

---

### Post by erictherev on 2010-01-24
In a Konsole, try the following commands:
```
sudo apt-get update && apt-cache search ndiswrapper
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by lidex on 2010-01-24
This should help:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
Scroll down to this section:
"2.2. Installing Packages (With Internet access on another computer)"

---

### Post by tacobeans1234 on 2010-01-24
I keep getting an error. Keep in mind that I don't have any sort of internet access through Ubuntu. I put the .tar.gz file that I downloaded off of the Ndiswrapper sourceforge website.

---

### Post by lidex on 2010-01-24
> **tacobeans1234 said:**
> I keep getting an error. Keep in mind that I don't have any sort of internet access through Ubuntu. I put the .tar.gz file that I downloaded off of the Ndiswrapper sourceforge website.

Right. You need the other two files. Download them all in Windows and follow instructions from link I posted.

As far as the error, can't help without more info.

---

### Post by tacobeans1234 on 2010-01-24
> **lidex said:**
> Right. You need the other two files. Download them all in Windows and follow instructions from link I posted.

As far as the error, can't help without more info.

Well thanks! I'm all installed thanks to you! Now I have another problem. When I try to run the -i command I get ```
couldn't create /ect/ndiswrapper/bcmwl5: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194
```Any ideas??

---

### Post by erictherev on 2010-01-24
The only thing I can think of is that perhaps you need root privileges to do this. Try preceding your command with "sudo" (without quotes).

---

### Post by lidex on 2010-01-24
> Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:

```
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils-*.deb
sudo dpkg -i ndisgtk_*.deb
```

Is that where you get the error? Did you install in the correct order?

---

### Post by tacobeans1234 on 2010-01-24
> **lidex said:**
> Is that where you get the error? Did you install in the correct order?

I have it installed.. My only problem is that I need to install my drivers now :P

---

### Post by lidex on 2010-01-24
Try this:
> If you chose to install ndisgtk, the graphical interface for ndiswrapper, after installation click on System  | Administration | Windows wireless drivers  and follow the instructions on-screen. For an idea of what to expect, some screenshots of ndisgtk can be found [here]("http://lxer.com/module/newswire/view/46385/").

If this works, and you have a network connection, then you can skip to Automatically loading at Startup - ndisgtk will load the driver if it installs correctly. 

Make sure that the INF file, SYS file and any BIN files are all put into one directory.

---

### Post by tacobeans1234 on 2010-01-24
> **lidex said:**
> Try this:


Make sure that the INF file, SYS file and any BIN files are all put into one directory.
Okay this is flippin' amazing. But, whenever I add the INF file, It says that the hardware isn't present for some reason.. Do I need to give it time, or something?

---

### Post by lidex on 2010-01-25
Reboot and try it again. If that doesn't work go back to that troubleshooting guide and follow the directions for blacklisting. There could be another driver accessing it first, in essence locking out your driver.

Here are some other links that pertain to your specific card:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G")
[http://ubuntuforums.org/showthread.php?t=581406&page=12]("http://ubuntuforums.org/showthread.php?t=581406&page=12")
[http://ubuntuforums.org/showthread.php?t=1017706]("http://ubuntuforums.org/showthread.php?t=1017706")
[http://ubuntuforums.org/showthread.php?t=224121]("http://ubuntuforums.org/showthread.php?t=224121")

---

### Post by tacobeans1234 on 2010-01-25
> **lidex said:**
> Reboot and try it again. If that doesn't work go back to that troubleshooting guide and follow the directions for blacklisting. There could be another driver accessing it first, in essence locking out your driver.

Here are some other links that pertain to your specific card:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G)
[http://ubuntuforums.org/showthread.php?t=581406&page=12](http://ubuntuforums.org/showthread.php?t=581406&page=12)
[http://ubuntuforums.org/showthread.php?t=1017706](http://ubuntuforums.org/showthread.php?t=1017706)
[http://ubuntuforums.org/showthread.php?t=224121](http://ubuntuforums.org/showthread.php?t=224121)

Oh silly me, I got the wrong driver file. I also can't find the correct one anywhere. Do you have any idea as to how to extract it from the EXE?

---

### Post by lidex on 2010-01-25
This should work:
> #

Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield.
#
If there are multiple INF/SYS files, look in the ndiswrapper list to see if there are any hints about which of them should be used.

# If you have Windows drivers on a cd and can't extract the INF file or the Bin files you can try installing the drivers on a Windows computer. Then look in control panel-system-hardware tab-device driver button. Then look for the device under network adapters. Once you have located the network adapter see what driver is being used by double clicking on the adapter in the list. Then go to the driver tab and click the driver information button. The driver and path will be listed it will usually be in C:/windows/system32/drivers folder. To be sure do a search for the file. The BIN file and INF file are usually the same name in the C:/windows/system32 folder. After you locate all the files copy to flash drive or burn to cd to move to Ubuntu computer for installation using Ndiswrapper.
# Make sure that the INF file, SYS file and any BIN files are all put into one directory. 

---

### Post by tacobeans1234 on 2010-01-27
> **lidex said:**
> This should work:

I'm still getting the Hardware Not Present :[.. Any Ideas?

---

### Post by lidex on 2010-01-29
Go back to this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
and read through it. Your next step I believe is to blacklist the drivers mentioned there.

---

### Post by tacobeans1234 on 2010-01-31
> **lidex said:**
> Go back to this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
and read through it. Your next step I believe is to blacklist the drivers mentioned there.
 Okay I've blacklisted everything it said to blacklist, and the hardware still isn't present. 
Grr this is frustratating. I won't give up until I can use internet! :D

---

### Post by lidex on 2010-01-31
Follow section 3.2 to get the chipset ID and then go here to find a suitable driver:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/List]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/List")


Troubleshooting - Have a look here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble")

---

### Post by tacobeans1234 on 2010-01-31
> **lidex said:**
> Follow section 3.2 to get the chipset ID and then go here to find a suitable driver:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/List](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/List)


Troubleshooting - Have a look here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble)
For some reason firefox has a problem loading the webpage.
Is there something I'm doing wrong?

---

### Post by lidex on 2010-01-31
WFM. Must be a local issue.

---

### Post by tacobeans1234 on 2010-02-03
> **lidex said:**
> WFM. Must be a local issue.
Is there another way to get the driver?
Possibly a torrent site, or something to that effect?

---

