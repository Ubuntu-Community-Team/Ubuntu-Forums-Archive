---
title: "I need some serious help"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by ibe2fly4chu on 2010-06-03
Alright here is the deal. I was using Ubuntu 9.10 Karmic. Loving it to the extreme. When i first installed it on my system, everything worked out of the box. However i updated to ubuntu 10.4 (running currently), and now my wireless card does not work. I am using a SMC2862w-g, part #:99-012084-449. I have looked high and low for the drivers to install and cannot find any that work...or any that i know how to install for that matter. I am a noob, so i do have trouble installing .tar.gz files. I was wondering if anyone might know a solution.....Also...if no one knows where to actually get drivers for this adapter on linux, if it were possible to somehow take the wireless drivers used in Karmic off the live cd and somehow copy them over to this new distribution....
thanks in advance!

---

### Post by Daddyo-613 on 2010-06-03
I'm not sure exactly what you're looking for but if you go to Applications>Ubuntu Software Center>type wireless in the search box a number of programs are listed that might help you.

---

### Post by SoFl W on 2010-06-03
[Here is a link]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&productCategory=5&modelNumber=585&partNumber=0&downloadType=1&knowsPartNumber=false") to the drivers/firmware page of SMC.

---

### Post by ibe2fly4chu on 2010-06-04
thanks for the reply. As for what i am looking for is simply a way to make this wireless card work. The drivers from the smc website does not support linux...or if it does then i am unaware of how to install it. As i said they wireless adapter worked perfectly with ubuntu karmic, however with 10.4 the computer cannot even detect that the wireless card is plugged in.

---

### Post by darkod on 2010-06-04
> **ibe2fly4chu said:**
>  The drivers from the smc website does not support linux...

Take a better look. In the link the other poster provided, in section Step 2 - What do you want do download, do you see the option Select OS? Inside there is Linux 2.6.x, and ubuntu 10.04 is using kernel 2.6.32.

Fill in the correct details about your card and see if this option will be available. That should allow you to download a linux driver.

Also, .tar.gz is just a compressed file, like .zip, it can have anything inside. You don't literary install the .tar.gz, first you extract it. Just right-click on it and select to be opened with Archive Manager and extract where ever you want.

The folder created during the extraction would usually have the driver files and a readme file with instructions how to install.

If you are lucky the driver might come as .deb file (when unpacked) and you can install .deb files by simply right-click and Install. But I don't think drivers come as .deb.

---

### Post by ibe2fly4chu on 2010-06-04
hmm...well i checked every possible option from the link provided while searching for the 2.6 linux drivers for the adapter...but all it returned was "sorry, nothing matched your search criteria"; this is after you fill in the information, select driver or firmware from the drop down menu, and select the part number which i stated earlier. I am still browsing google for a possible driver...lol i must have downloaded at least 2 viruses while looking T.T. Thanks again for the reply, i do appreciate all the help and the advise on the .tar.gz files. Anyone have any more suggestions? arr this is getting frustrating...

---

### Post by darkod on 2010-06-04
I was hoping the manufacturer will provide the exact driver, not to go the long way around. But if that doesn't work, boot ubuntu and in terminal execute:

If your adapter is USB:

lsusb

If it's integrated or installed in PCI slot:

lspci

That will list all devices on the USB or PCI bus, so it might be large output. Find your SMC device in it and write down the line describing it, all of the characters (some of them are code for the exact chipset used). Then we can search for driver/instructions according to the exact chipset which might even not be produced by SMC.

Just to give you idea how lsusb output looks, here is mine (lspci is much longer):

darko@darko-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID [COLOR=Red]0518:0002 EzKEY Corp. EZ-9900C Keyboard[/COLOR]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The ID code can also help finding the information exactly for your device. Try to find your device in the output and use google, or let us know if you need help searching for the driver.

---

### Post by ibe2fly4chu on 2010-06-04
okay, i followed your instructions.. the output was:

Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 005: ID 1260:ee22  [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR="Black"][/COLOR]
i highlighted the one i believe is the adapter, and to make sure i did one with the adapter plugged in, and without; after which that was the only device that appeared and vanished when the adapter was plugged in and out.

---

### Post by darkod on 2010-06-04
Hmm... it's not recognized as any particular type. Lets google a bit.

---

### Post by darkod on 2010-06-04
Do you know french or someone who speaks french? This seems to have an answer, but i can't get it exactly:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=3510547](http://forum.ubuntu-fr.org/viewtopic.php?pid=3510547)

Even though you can see the commands, I'm not sure it would work without understanding what they are saying in between. :)

---

### Post by ibe2fly4chu on 2010-06-04
no unfortunately i dont. lol i will try to see what i can make of it using google translate though.

---

### Post by darkod on 2010-06-04
Another idea is connecting the machine to the internt with a cable temporarily, and try to find driver with ubuntu in System-Administration-Hardware Drivers.

---

### Post by ibe2fly4chu on 2010-06-04
Alright, from what i could salvage using google translate..He has pretty much the same problem as me. The other user told him to do the same lusb command to get the chipset and it showed up the same result as mines. Shortly there after the helper advised the person with the problem to use nidswapper however the person with the wireless adapter then asked how can he get the packages in offline mode (seeing as how his adapter isnt working)..then the post ends...so yea..lol pretty much where we are as well T.T

---

### Post by darkod on 2010-06-04
But somewhere in the middle of it, the adapter started to be recognized more properly, and maybe that's the problem you have too. Your lsusb results give just the ID, but not manufacturer and model. In that thread, the adapter went from:

Bus 001 Device 005: ID 1260:ee22 (same as yours)

into

Bus 001 Device 002: ID 1260:ee22 Standard Microsystems Corp. SMC2862W-G v3 EZ Connect 802.11g Adapter [Intersil ISL3887]

Not sure if that was after the:

sudo update-usbids

or something else was needed manually to change in post #7 in the first code box with all that hardware descriptions.

Try the above command first, it sounds like it is updating the IDs (usb id -> update-usbids )

PS. But not sure if you need to be connected to the internet for that. Can you use wired connection to help you sort this out?

---

### Post by ibe2fly4chu on 2010-06-04
hmm i see what you mean. I did the command however all it returned was "unable to resolve host address 'www.linux.org'
update-usbids: download failed 

i was thinking...since this other guy had the same exact problem, with the same type card, think we could assume i am using the same chipset and use his card version? going to try some more of the update usb commands, but so far i havent gotten any information

---

### Post by darkod on 2010-06-04
> **ibe2fly4chu said:**
> hmm i see what you mean. I did the command however all it returned was "unable to resolve host address 'www.linux.org'
update-usbids: download failed 


As I suspected, it wants to connect to [www.linux.org](www.linux.org) to get new IDs probably. You need internet connection working to run it.

---

### Post by ibe2fly4chu on 2010-06-04
I am just ready to give up. I mean if the adapter worked fine out of the box on karmic, i really dont see a reason why its not in this new distribution. I been looking for about 3 days now and to be honest its fustrating and dumb. Its not even to say i mind the searching, but for almost EVERY function attempting to fix the stupid thing it requires an internet connection; ironically not having an internet connection being the problem in the first place. Ubuntu nice and all, but i mean if its this much trouble to simply get on the internet i just dont know...Thanks for all the help.

---

### Post by T-rock007 on 2010-06-04
You know the best way to upgrade is to just backup your data and do a fresh install.Thats what I do.I never have any problems.

---

### Post by darkod on 2010-06-04
> **ibe2fly4chu said:**
> I am just ready to give up. I mean if the adapter worked fine out of the box on karmic, i really dont see a reason why its not in this new distribution. I been looking for about 3 days now and to be honest its fustrating and dumb. Its not even to say i mind the searching, but for almost EVERY function attempting to fix the stupid thing it requires an internet connection; ironically not having an internet connection being the problem in the first place. Ubuntu nice and all, but i mean if its this much trouble to simply get on the internet i just dont know...Thanks for all the help.

While I understand your point, it's definitely not that simple. And it doesn't necessarily mean that the new version of ubuntu works the same as an older one, and will support the same hardware out of the box.

On top of that, you saw yourself that SMC doesn't offer drivers for 2.6.x, so as usual, it's up to the linux community to try and create them, while it should be hardware manufacturers job. They scramble in a hurry to create drivers for windows OS, but don't care too much about linux. Is win7 better because of that? They simply include drivers that the manufacturer provided.

Also, this adapter seems rather old, I found some threads from 2006. After a while manufacturers will stop supporting hardware to make you buy new hardware. :)

Even for windows support that is true. I remember I has D-Link adapter, DWL-122 or what ever, bought with XP drivers. Later when vista came out, there was a driver although unsigned (so during install it was complaining), but for win7 there is no driver at all. There is no way to make it work under win7 as far as I know, unless I program drivers myself. Why didn't the vista driver just work? :)

They simply showed no intention to keep making drivers.

I asked few times can you use wired connection, you never commented anything. If the wi-fi router is in your house, most of them would have 4 wired ports that you can use to get internet access and see if you can make the usb adapter work.

As far as 9.10 is concerned, have in mind that it's only supported for one more year, so you would need to start thinking about Lucid at one point or another.

---

### Post by cariboo on 2010-06-04
If you are running a 32-bit version you could probably get the device working using ndiswrapper. have a look [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for info.

The files you need are located on the Live CD in /pool/main/n

---

### Post by ibe2fly4chu on 2010-06-04
Aright. Good news Everyone! I finally got it working after refusing to give up. Alright for those with this wireless card i shall state what worked for me:

First and fore most if you are on Ubuntu 10.4 you need ndiswrapper to make this work. 

I did it the Command line way however it took forever, and after experimenting i found an even easier way.

First i took the advise from a user in this thread and poped my ubuntu karmic live cd in ( this is while i was logged into ubuntu 10.4 if you are wondering.) Then simply open the cd, go to pool /pool/main/...here you will find ndiswrapper .deb files. The reason why i recomend using this is because chances are you dont have internet while doing this, so downloading it via command line is out of the option. After you install Both the common scripts needed to run ndiswrapper AND the GUI interfeace, go to terminal and type  	"ndisgt"..which will then bring up the GUI for ndiswrapper. At this point you will want to go to SMC's website and download the correct WINDOWS driver for your adapter/card. After extracting it you will find multiple driver versions under the DRIVER folder. The windows xp version of the driver worked fine for me. However if one does not work simply just rotate through all 4 versions till one work.

Also key thing to note, when choosing a driver to install...you want to choose the .inf file...

---

### Post by darkod on 2010-06-04
Great job. We are all proud of you. :)

---

