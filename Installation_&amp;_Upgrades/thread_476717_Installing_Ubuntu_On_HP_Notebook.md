---
title: "Installing Ubuntu On HP Notebook?"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by theexbrit on 2007-06-17
Hi all, I have an HP Pavilion tx1119us notebook with Vista Home Premium installed. I really dont like Vista & I'd like to install Ubuntu or Libspire or some other Linux distro. Which would be best for this comp & would I encounter any hassles?

*  AMD Turion 64 X2 mobile TL-56 / 1.8 GHz Cache Memory
* DDR II SDRAM 2 x 1 GB
* Serial ATA
* 160 GB Hard Drive
* DVD±RW (+R DL) / DVD-RAM
* LightScribe Technology
* 5 in 1 card reader
* 12.1 in TFT active matrix
* 1280 x 800 ( WXGA)
* NVIDIA GeForce Go 6150

Thanks.

---

### Post by jimrz on 2007-06-17
> **theexbrit said:**
> Hi all, I have an HP Pavilion tx1119us notebook with Vista Home Premium installed. I really dont like Vista & I'd like to install Ubuntu or Libspire or some other Linux distro. Which would be best for this comp & would I encounter any hassles?

*  AMD Turion 64 X2 mobile TL-56 / 1.8 GHz Cache Memory
* DDR II SDRAM 2 x 1 GB
* Serial ATA
* 160 GB Hard Drive
* DVD±RW (+R DL) / DVD-RAM
* LightScribe Technology
* 5 in 1 card reader
* 12.1 in TFT active matrix
* 1280 x 800 ( WXGA)
* NVIDIA GeForce Go 6150

Thanks.

Welcome

since this is the ubuntu forum, i would suggest ubuntu 7.04 feisty fawn. unless you are actually using some 64 bit apps, i would recommend using the 32 bit version as it has fewer issues and runs very nicely and blazing faston my core2duo E6600. i would also suggest downloading and running the "live cd" to get a feel for ubuntu and see how it works on your specific hardware. you might also try "live cd's" from other distros that you are thinking about and give them a try, as well. one caution about "live cd's" is that they run quite a bit slower than a full install because they run (in ram) from the cd/dvd drive only. after you find which distro you are most comfortable with, have a go at it.

not sure about your card reader, but the rest of your listed hardware should be well supported. 
you might want to check the specs on your wifi card to find the make/model,chipset and search these forums to see what results others are getting. some cards are bit of a pain, though most can be made to work, while many "just work" out of the box.

---

### Post by serxubuser on 2007-06-17
* AMD Turion 64 X2 mobile TL-56 / 1.8 GHz Cache Memory -- intel core duo t2050 1.6ghz
* DDR II SDRAM 2 x 1 GB                                                 -- ddr2 sdram 2 x 512mb
* Serial ATA                                                                   -- serial ata
* 160 GB Hard Drive                                                       -- 100gb hdd
* DVD±RW (+R DL) / DVD-RAM                                           -- 8x DVD±RW (+R DL) cdrw
* LightScribe Technology                                                 -- lightscribe technology
* 5 in 1 card reader                                                        -- 5in1 cardreader
* 12.1 in TFT active matrix                                               -- 15,4'' tft                           
* 1280 x 800 ( WXGA)                                                      -- 1280 x 800 wxga
* NVIDIA GeForce Go 6150                                               -- intel 945gm express
                                                                                    -- etc


-- successfully installed xubuntu7.04
-- with restricted driver ipw3945abg wireless
-- 915resolution/auto915resolutionscript to enable 1280x800 resolution (only intel chipset 8xx/9xx for as far as i know

-- not tested: 
----5in1 card reader
----light scribe
----docking port
----expresscard/54pc card slot
----type 1/2pcmcia pc card slot

---

### Post by Caveben on 2007-06-17
I have the same system and am having trouble installing. It hangs after the initial boot screen with the pretty ubuntu logo and doesn't want to do anything else. I have got the live cd to boot once or twice before but it won't boot up again. 

Does anyone have any suggestions?

Thanks

---

### Post by merlinus on 2007-06-17
Safe (Video) Mode, or the Alternate Desktop installation cd.

-merlin

---

### Post by Caveben on 2007-06-17
It will boot in safe mode. If it won't boot in normal mode from a cd, will it be able to boot when it is installed? :confused:

---

### Post by merlinus on 2007-06-17
Yes.  If you have video problems, post about them, and someone will point in the right direction to obtain and install the necessary drivers.

Or you can do a Search for your particular card.

-merlin

---

### Post by theexbrit on 2007-06-25
Caveben, if you're still having trouble, download the alternate desktop install. It worked for me!! Now I just have to figure out how to get my sound & networking up 'n running.


> **Caveben said:**
> I have the same system and am having trouble installing. It hangs after the initial boot screen with the pretty ubuntu logo and doesn't want to do anything else. I have got the live cd to boot once or twice before but it won't boot up again. 

Does anyone have any suggestions?

Thanks

---

### Post by HarshReality on 2007-06-25
Good luck getting that card reader to work its a kernel wide issue across several distros.. of course if you pull off some magic by all means share ;)

---

### Post by Old *ix Geek on 2007-06-25
> **HarshReality said:**
> Good luck getting that card reader to work its a kernel wide issue across several distros.. of course if you pull off some magic by all means share ;)Really?  One of my HP desktops has a 5-in-1 card reader, and I did NOTHING to get it to work.  It just did. :confused:  (FWIW, that particular computer still has Hoary on it.)

---

### Post by heyhey on 2007-06-26
Card Reader: For certain models with "Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller", check out here: 

[http://ubuntuforums.org/showthread.php?p=2635321](http://ubuntuforums.org/showthread.php?p=2635321)

---

