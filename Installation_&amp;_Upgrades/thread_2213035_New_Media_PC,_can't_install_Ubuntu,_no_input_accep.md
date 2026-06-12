---
title: "New Media PC, can't install Ubuntu, no input accepted"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by I.Bun.Tu on 2014-03-24
I just bought the following parts to build a Media Centre PC:

Corsair Vengeance Pro (2x4GB) ddr3 1600mhz cl9 dimms
AMD X6 FX-6300 (6 core, 3.5ghz, 8mb cache)
Gigabyte GA-970A-D3P AM3 socket mobo
Sapphire Radeon R7 260X OC 2gb, 1150mhz clock, 6600mhz memory

I threw everything together and booted into the BIOS and everything worked fine. It asked for some installation media and I fed it a Ubuntu 13.10 DVD.

I knew the R7 260X was a new card and did a little research in the store before buying where this article: [http://www.phoronix.com/scan.php?page=article&item=sapphire_r7_260x&num=1](http://www.phoronix.com/scan.php?page=article&item=sapphire_r7_260x&num=1) lead me to believe that the video card should be well supported in Ubuntu (I didn't even want to get a video card but didn't have much option for AM3+ boards with on-board HDMI).

My problem is that when trying to install, everything freezes are the first page. There is no mouse on the screen and I don't get any response from mouse and keyboard input. The main dialogue to select installation language is where it freezes. Except it's not really frozen because the screen saver kicks in after a certain amount of time. The mouse and keyboard work fine on other computers and the keyboard is fine for navigating the BIOS. If I select to try Ubuntu instead of installing, I'm taken to a black screen with a dialogue that says it is starting Ubuntu in low graphics mode but I still can't give any more or keyboard input so I can't get past this screen.

I also tried installing from Ubuntu 12.04 LTS DVD and had the same problem except that I could see the mouse pointer in the middle of the screen. I just couldn't move it. I saw in the article that the R7 260X was tested with a daily build of 14.04 so I downloaded 14.04 to give that a try. I will let you know how that works but it would be great to get this working with a stable release of Ubuntu.

Please let me know any more information that I can provide. Thanks.

---

### Post by I.Bun.Tu on 2014-03-24
So it turned out the problem is that Ubuntu does not detect all of the USB ports. None of the USB2 ports seem to work and the 4 USB3 ports work sometimes and interchangeably (as in some work sometimes but none of them work consistently).

I was able to get Ubuntu 13.10 installed (although the open source drivers don't support my video card). The USB2 ports are still not working while the USB3 ports work intermittently. Ethernet appears to have an issue (I will note that all the USB ports work fine before Ubuntu is loaded, i.e., for connecting a keyboard to navigate the BIOS) as well. So far the best results I've had are installing a daily build of trusty tahr which supports my video card open source but stopped booting after the 3rd reboot and still has USB and ethernet issues. Right now I'm going to try copying AMD's proprietary drivers to a USB and try installing them in a Ubuntu 13.10 installation via tty.

I would really appreciate some advice on continuing to troubleshoot. If I should get a new mobo, please let me know. Thanks for reading.

---

### Post by mastablasta on 2014-03-25
the graphics issue is logical to me. the card was not out or just came out when 13.10 was made. 14.04 is next LTS so eventually going wiht that is the way to go anyway. opensource drivers with such a new card? while even the proprietary driver porbably don't support all features yet how could oyu expect that the reverse engineered opensource drivers would ? :-)


motherboard and USB this one is more unusual. Gigabyte is usually supported in linux. however in this case it looks like some drivers are missing. when you do get it to boot i suggest checkign the logs for any errors. if the mobo is newer model i suggest upgrading the BIOS/firmware. driver in linux are usualyl built into kernel so if this mobo is newer than the current kernel then you need newer kernel or if they have some linux drivers you might be able to patch the currently installed kernel with the drivers.

according to this page[http://ee.gigabyte.com/products/page/mb/ga-970a-d3prev_10/](http://ee.gigabyte.com/products/page/mb/ga-970a-d3prev_10/):

[LIST=1]
[*][COLOR=red]Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website.[/COLOR]
[/LIST]

also the usb chipset is : VIA VL805 chip and South Bridge.

edit: have a look at this thread if you find anything interesting: [http://ubuntuforums.org/showthread.php?t=2111223](http://ubuntuforums.org/showthread.php?t=2111223)

32bit should work :-O

one more edit  - fix is here: [http://ubuntuforums.org/showthread.php?t=2111223&page=4&p=12851568#post12851568](http://ubuntuforums.org/showthread.php?t=2111223&page=4&p=12851568#post12851568)

---

### Post by I.Bun.Tu on 2014-03-26
Thank you for the reply. As a trouble-shooting measure I installed Windows 7 to check functionality. I would once again like to note that all of the USB ports work fine for plugging in a keyboard to control the BIOS.

As soon as the Windows 7 installer loaded, I lost my USB functionality and had to go through the installation with a PS/2 keyboard. After installation I still had no USB functionality until installing the USB drivers from the driver CD included with the mobo. After all drivers were installed, everything functions fine in Windows 7.

From further research I've gathered that the latest proprietary driver from AMD should work fine in Linux, if not the BETA will for sure, so it looks like I think I have the graphics sorted. I will report back after I'm able to try installing these drivers.

As far as USB and Ethernet is concerned I will try the fix in the post you mentioned and get back to you. Thank you very much for your help.

---

### Post by Mark Phelps on 2014-03-26
I have recently installed an R7 AMD card and can attest that the AMD 14.1 and 14.3 drivers work well with it.

I was also able to get the Radeon drivers to work but, that was with the following limitations:
1) Could only get one screen working (have two) -- required "nomodeset" for that to work
2) Could get both screens working (using "xforcevesa") but then discovered that could not do any work requiring "sudo".

---

### Post by I.Bun.Tu on 2014-03-26
Thanks for the info Mark Phelps. I downloaded the 14.3 Beta driver .zip from ATI's website. Upon extracting, the file I got was an Amd catalyst 13.35 driver installer which ran fine and when I launch Ubuntu 13.10 I get an apport error but I think the graphics are okay until Trusty Tahr comes out in a few weeks. I am using one monitor dvi>vga output and a TV HDMI output. The HDMI audio is insanely distorted but the mobo has onboard optical and that is actually working good for me. So I am not having the same issue as you with two screens fortunately. 

I wouldn't mind troubleshooting the HDMI audio because I have other rooms I want to use this system in that do not have sound systems with optical input.

Thank you very much for your help mastablasta, that article definitely helped me out. I initially tried setting my IOMMU Controller in the BIOS to Enabled because it was disabled. This enabled all of my USB 2.0 ports, but left my USB 3.0 ports disabled. I also tried adding the iommu=soft protocol to GRUB and disabling the IOMMU Controller as suggested in the post you linked. This enabled the USB 3.0 as the poster indicated but i'm pretty sure they are just functioning as USB 2.0 ports because I can only get 30mb/s transfer speeds that I usually get on USB 2.0 devices as opposed to the 60-100mb/s transfer speeds I receive from USB 3.0 devices on other systems (i.e., I'm transferring files from external usb3 hard drive on my laptop with ubuntu 13.10 @ 60-100mb/s and usb2 drives transfer at 30-35mb/s; plugging the same usb3 external hard drive into the desktop discussed in this thread, into a usb 3.0 port, produces transfer speed of 30-35mb/s).

I don't know if I should change the thread to solved yet. I got Ubuntu installed with the AMD beta drivers. My USB ports are working and so is my ethernet. I just need my USB 3.0 ports transferring at the right speed and my HDMI audio working, but I imagine the HDMI audio might be related to the Beta driver. I shouldn't create a new thread for the USB 3.0 port issue should I? Thank you for all the help so far btw. You have helped me make my system usable.

---

### Post by mastablasta on 2014-03-27
you could join in the discussion in the previous thread. i was hoping that USB fix will work. hmmm i would post a bug about this on launchpad see if any of the developers can pick it up or resolve it.

i can't give much regarding HDMI. you could try to look if anyone else had this issue. again it might be worth reporting a bug but AMD driver bugs are reported elsewhere (on AMD site?!)

if you have some time on your hands you could also try 14.04. It's still in beta, but some say it is preety stable already. it comes with a much newer kernel.

on thing to note is that AMD releases it's drivers sort of simultaneously with new Ubutnu release. so it means they owudl be happy on any feedback for beta drivers. i mean if they don't know anything is wrong how can they fix it? 

windows and manufacturers for windows pay people to test new things, but in linux users are often testers at the same time :-)

regarding thread - getting help is much faster if issues are separated and each issue with specific and descriptive title. that way people that are experts in sound issue can jump in HDMI thread, people that know more about graphics will jump in GPU thread. For example i never frequent development and programing part of forums since i really do not know much about that. :-) people there might not look into abosulute beginers section etc.

have a look on this informative thread on how to provide better information and get a faster reply on particluar issue: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by I.Bun.Tu on 2014-03-28
Thanks for all the help. It seems that my USB 3.0 is working mostly. I can get 120-80mb/s from external usb3 hdd to internal hdd, but from one external usb3 hdd to another (both WD MyBooks) the transfer is only 30mb/s. I have a laptop running Ubuntu 13.10 doing the same thing and achieving 80+mb/s transfer speeds, so this is a little weird but a separate issue which I will try to resolve on my own but is low priority. I will also let AMD know about the audio for the beta drivers.

I will change the thread to solved.

For anyone looking for the solutions that worked for me:

**Issue #1: **Could not install Ubuntu because no input could be given (USB ports and ethernet were not working correctly)

**Solution:** Plug in a PS/2 keyboard or set IOMMU Controller to Enabled in order to be able to give input. Once Ubuntu is installed edit /etc/default/grub and change GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="iommu=soft" then update-grub and disable IOMMU Controller in BIOS (if it was necessary to enable in order to do installation with USB keyboard/mouse).

gksu gedit /etc/default/grub
sudo update-grub

**Issue #2:** Ubuntu 13.10 boots to low graphics mode but Ubuntu 14.04 daily builds boot to normal graphics

**Solution:** AMD Radeon R7 260X is very new and currently only works with AMD's proprietary Beta drivers (I could not get graphics working with the stable proprietary driver), the Ubuntu 13.10 open source drivers do not support the R7 series of Radeon cards, Ubuntu 14.04 open source drivers DO support Radeon R7 series cards.

Once Ubuntu 13.10 is booted: ctrl+alt+f2 (or however you want to get to a tty)
mkdir amddrivers && cd amddrivers
wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' [http://www2.ati.com/drivers/beta/Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip](http://www2.ati.com/drivers/beta/Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip)
unzip Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip
cd fglrx-13.35.1005
chmod +x amd-driver-installer-13.35.1005-x86.x86_64.run
sudo ./amd-driver-installer-13.35.1005-x86.x86_64.run

Go through the installer and select option to install general debian based driver. I had better luck with this than trying a distribution specific build. After installation is complete, reboot and Unity should load in Ubuntu 13.10 (albeit with some errors maybe).

Thanks again for the help guys. I hope this thread is able to help anyone else with similar issues.

---

### Post by frank18 on 2014-03-29
Why you do not install Ubuntu14.04  instead of 13.10 and will solve the drivers problem for sure.
14.04 is already running same as LTS, and it's pretty fast too.

---

