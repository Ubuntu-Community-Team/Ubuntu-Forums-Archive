---
title: "SIS graphics: Cannot install."
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by eduardoflsantos on 2014-03-05
Hi,

I'm a Ubuntu user, and I am trying to install Lubuntu in a old machine that has Windows XP.

I download in and burned the CD. Then I rebooted it and loaded the CD. Everything went fine, I could select the language and choose to install Lubuntu (13.10).

But in the process of loading the files, there are lots of errors:

[http://s29.postimg.org/apfuj3neu/2014_03_05_17_29_34.jpg](http://s29.postimg.org/apfuj3neu/2014_03_05_17_29_34.jpg)

[http://s24.postimg.org/m4rhqz6s4/2014_03_05_16_14_58.jpg](http://s24.postimg.org/m4rhqz6s4/2014_03_05_16_14_58.jpg)

[http://s14.postimg.org/h033u2zjk/2014_03_05_17_16_13.jpg](http://s14.postimg.org/h033u2zjk/2014_03_05_17_16_13.jpg)

Once it actually finished to load (with errors), and than it stood like this:
[http://s8.postimg.org/stivl6kyb/2014_03_05_17_32_04.jpg](http://s8.postimg.org/stivl6kyb/2014_03_05_17_32_04.jpg)



Any ideas on what the problem might be?

Thank you.

---

### Post by Bashing-om on 2014-03-05
eduardoflsantos; Hi !

If it were me I would:
Download the .iso file once more -> verify it's integrity ;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn the disk at the slowest possible rate ;
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Boot the liveCD to the boot options screen and;
"check disk for defects"

Then -> try once more to install
I have greater success installing Lubuntu if I do not check the boxes for installing updates while installing, and install 3rd party software.
These can be done after the install completes AND if you do require the proprietary drivers.

[INDENT][INDENT]been there
[INDENT][INDENT][INDENT]done that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-05
[ 						 							]("http://ubuntuforums.org/member.php?u=1111508")Hi Bashing-om

Thank you for your reply.

I used Furious ISO Mount to check the checksum, and it did not match with this one:
[http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/SHA256SUMS](http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/SHA256SUMS)
3548234515263ce6334097ceb0c2dd3858873b0ed826dd5d43fdaeca9c27fae0 *lubuntu-13.10-desktop-i386.iso
So I deleted the file, and downloaded in again via torrent (from the official website). Then I used the [manual check]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_with_.22Checksums_calculator.22"), using the terminal to find the checksum, and it gave me the same checksum I had before, that does not match with the [oficial checksum]("http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/SHA256SUMS"). 

My checksum:
5e85e368b6eaf1b9f5cf88467c6570f5

I google it, and it correspondes to this:
[http://ubuntuforums.org/showthread.php?t=2151890](http://ubuntuforums.org/showthread.php?t=2151890)

> 
[SIZE=4]**'grub-n-iso'**[/SIZE]

  **Detailed description**

 You find the detailed description at [grub-n-iso]("https://help.ubuntu.com/community/grub-n-iso") 
 
**Advantages**



[LIST]
[*]Similar to normal installation (via 1GB or 2GB USB drive)
[*]No upgrading between versions is necessary
[*]Full flexibility, for example to make a dual boot system
[*]The official Lubuntu i386 desktop iso file is used, and can be checked with **md5sum**
[/LIST]



I have downloaded it twice, got the torrent from [here]("http://lubuntu.net/"). Did I get the wrong version?

Thank You

---

### Post by Bashing-om on 2014-03-05
eduardoflsantos; Welp.

For sure for sure the hash sums must match. 
There are three algorhythms one may use, I always use md5sum personally. (maybe you are mixing md5sum and shasum )
 As to the proper version - uhhh, does your CPU support PAE ?
If it does then a current install release should work; not saying the alternate install would not work "better".
Else, you will have to take the long slow bandwidth expensive method to get to the latest version as detailed in the link you found.

I have never had to resort to any other means to download the .iso image other than 'buntu and I always verify that .iso with the terminal command "md5sum" and check that output ->
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
So, can not directly advise on any alternate method.

A thought: Have you got an older liveCD of 'buntu on hand ? Maybe try and download the .iso from the liveCD and verify the md5sum from the terminal ?

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-05
Hi Bashing-om,

Just noticed, my checksum matchs the one from the link you gave me in your last post! So there is nothing wrong with it ;)

I was comparing it with [this checksum]("http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/SHA256SUMS") information I found googling, which is probably from some older versions of Lubuntu 13.10, I don't know, and it didn't match.

But the link you gave me matchs my checksum xD


So, I have burned a new CD at slow speed rate and I will try again tomorrow. Maybe I had some problem burning the CD, or the CD was too old and got damaged (I rarely burn CDs nowadays, so I have these never-used CDs for quite some years now xD) 

I will "check the disk for defects" too. And as a backup plan, I will also take a DVD with Mint ;)
 

Thanks again, I will let you know if I succeed using your sugestions ;)

---

### Post by Bashing-om on 2014-03-05
eduardoflsantos; Making progress !

I will be here tomorrow too, I fully expect.

Will see how things work out for ya.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-05
On an unrelated note, I think I found an error on Lubuntu documentation.

In [Lubuntu instructions]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"), they say:

> Alternative Install
Alternate  ISOs are for low-RAM PCs. Computers with **less than 400 MB of RAM** are  considered low-RAM computers. You can find more information  about  Alternative Install [here]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")
The "here" is a link to alternate ISOs page. There, it says:

> Alternate ISOs are for low-RAM PCs. Computers with** less than 700 MB of RAM** are considered low-RAM computers.

Compare the sentences in bold.

I *think* my PC has 512 RAM, and I had read the 400MB sentence, so I burned the normal ISO. But if the second page is correct, I should have burned the alternate ISO for low-ram PCs. I see I'll probably have to burn a 3rd CD. :P . I have to check that tomorrow. Anyway, I'll survive :D. But it might be a good idea to correct whatever page is wrong.

---

### Post by Bashing-om on 2014-03-05
eduardoflsantos; Hey,

That discrepancy is not good. Will try and get that to the documentation team and get it taken care of.
Appreciate the heads up.

mean while back 
[INDENT][INDENT]at the ranch
[/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-06
Hi Bashing.

No sucess. Yet :P

I used the new CD, and got to the menu, choose to install, and this time I saw the blue page write, and even a bluewish desktop imagem. But it kept changing between a black screen and that background image (with the cursor visible). And nothing happened, it just keep switching between those 2 images.

I entered in Windows XP instalation and check what hardware I got:
Celeron (R) CPU 2.40 GHz, 0.99 RAM GB (? lol)
Can't figure out what his the graphic card, it says: SiS 650_651_M650_M652_740

Its not a too bad PC, I think...

I also tried the "check disk for defects". No errors found.

Maybe I can try other Ubuntu family distros. Which one would you recomend for an Office desktop where the main goals would be running as fast as possible and performing normal office task such as use LibreOffice and Firefox for internet? I don't need or want good visuals or customizations, I prefer more performance xD 
Maybe Xubuntu?

I'll try Mint for now...

---

### Post by mörgæs on 2014-03-06
Here's some advice on dealing with SIS graphics:
[http://ubuntuforums.org/showthread.php?t=2209318](http://ubuntuforums.org/showthread.php?t=2209318)

---

### Post by Bashing-om on 2014-03-06
eduardoflsantos; Yuk ! SIS graphics.

Not to well supported and problematic in linux . However, several have been able to make it work, but do heed mörgæs' advise.
These threads also apply, and presently I can not add to the aggregation of knowledge in this respect:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)
[http://ubuntuforums.org/showthread.php?t=2172375&page=8](http://ubuntuforums.org/showthread.php?t=2172375&page=8)
[https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

If you choose to continue to attempt to install Lubuntu I will be more than glad to assist in any way I can; Though my knowledge and assets are limited . It is a real trial to get SIS graphics functional, -in my experience - to say the least.

Just as a thing to consider:
If this is a desk top machine, and you have access to a PCI graphics card, install a different card. (old cards are cheap - I paid $15 USD for the card (ATI) that I am running with excellent results with the open source driver).

Whatever you decide we will do.
[INDENT][INDENT]there is always room
[INDENT][INDENT][INDENT]to learn more
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-06
Now all makes sense, because I was unable to install Mint 13 and 16 neither. I was about to try Xubuntu, mas I guess it's useless...

My hardware knowledge is very limited, and I don't even have the tools to open the PC in here (it's a big desktop, yes). Tomorrow I'll check if I can change the graphic card. I don't really need a good one, I just need one that has no problems with Linux ;)

Thanks again guys.

---

### Post by ibjsb4 on 2014-03-06
There are three types of video card slots.  PCI, AGP and PCIe

[http://www.ehow.com/about_5420574_types-graphic-card-slots.html](http://www.ehow.com/about_5420574_types-graphic-card-slots.html)

---

### Post by eduardoflsantos on 2014-03-06
Hi again.

I discover, with some help, that my graphic card is onboard :/

Anyway I can "disable" it, and use an external one?

I have a lighter :P

These are the free slots I have:
[http://s27.postimg.org/ff2zbxg03/2014_03_06_16_11_33.jpg](http://s27.postimg.org/ff2zbxg03/2014_03_06_16_11_33.jpg)

Is it a PCI and a AGP slot?

It would be very nice of you could to tell me if it is, and what to keep in mind when buying some old graphic card (I already know I should keep away from SiS xD). How do I know what to buy? 

Thanks

Edit: A [better image]("http://s24.postimg.org/ecttj1nj9/2014_03_06_16_45_57.jpg")

---

### Post by ibjsb4 on 2014-03-06
Is a pic worth a 1000 words :)

[ATTACH=CONFIG]250896[/ATTACH][ATTACH=CONFIG]250897[/ATTACH][ATTACH=CONFIG]250898[/ATTACH]

---

### Post by Bashing-om on 2014-03-06
eduardoflsantos;

See ibjsb4's last:
You will get a much better experience (updated technology) using an add on card. Take your time and choose wisely. - Compatible with your monitor -

Once you have determined what type of card you can install, it is a piece of cake to do so - in a desk top machine - !
Make sure that the cable to the monitor you have is suitable for the card. (PCIE is the higher end better card )
During the procedure do not touch the circuit board of the video card with your fingers, and do not stand on carpet while working on your machine (static charge ! will blow components ), just make sure you have touched a ground to discharge any static charge you may have picked up. No metal tools inside the machines case is allowed -> no possibility to short anything out !

Generally: 2 phillips head screws at the back of the side panel(s) are to be removed. Slide the panel(s) back a bit to disengage the locking tangs (pay attention to how these tangs do engage). Your first time doing this I would suggest removing both panels for visibility reasons.
See what slot the card is going to be inserted into, and remove the case covering at the back of the case.
Insert the card into the appropriate slot (any locking levers ?) - The card can not be inserted in a wrong motherboard slot - just pay attention to where the alignment slot on the card is in respect to the corresponding tang in the card position slot. Some small amount of effort to insert the card but do NOT ForcE.
The AGP PCI and or PCIE slots for the card will be to the rear of the main board such that when a  cover on the case  is removed the card's monitor connector protrudes from the back. 

That said, if ya want to mess with the on-board SIS graphics, well, we can give it a whirl. Won't hurt to try, as all is lost is time and effort.

We do what we can to get you
[INDENT][INDENT][INDENT]up and running 'buntu
[/INDENT][/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-06
Now that's more specific than the previous link :P

But it's still hard for me to identify them xD

The brown seems an AGP 2.0 (although the right side is different). And the white one seems a 5V PCI 32 bits.

---

### Post by ibjsb4 on 2014-03-06
If you can tell us the make and model of your computer, the motherboard could then be looked up.

---

### Post by Bashing-om on 2014-03-06
eduardoflsantos; Hey;

Still following, ibjsb4 doing such a great job.
Certainly better than I can do !

[INDENT]no substiture for the knowledge
[INDENT][INDENT][INDENT]and experience
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-06
Bashing, I had missed your other post, because we posted almost at the same time. ;)

I don't want to spend much money on this. I have other 2 old desktops at home, I'll check if I can use something from them. If not, i'll buy a second hand graphic card.

My monitor is VGA.

Thank you for your fine explanation. No doubt it would be usefull ;). But before going to take that step, can you please confirm me that if I use an addon graphic, the onboard one will not give me the same problems anyway? Is there a way to "neutralize" it?

ibjsb4, it's a City Desk. Model: Luso PC Celeron. This seems a random name that some portuguese shop gave it (I'm from Portugal, and "Luso" is a prefix that means from Portugal). They probably just used to buy the componentes, assemble, and sell the PCs.

---

### Post by Bashing-om on 2014-03-06
eduardoflsantos; Well;

ibjsb4 has broached an interesting point that I had not considered, that there is a difference in the card slot for 32/64 bit hardware.
-my 64 bit PCI slot looks identical to your PCI slot - I am comparing on an Abit mother board to your Asrock. Great board by the way.

As your motherboard is Asrock, it is safe to say the box was built locally. Let's do this -> get the identification numbers off of the motherboard and we can hunt up the manufacture's manual for it.
( Hint: I bought my ATI card NEW for $15 - free shipping -, may pay to "shop around" - time permitting) 

[INDENT][INDENT]when in doubt
[INDENT][INDENT][INDENT]read the directions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2014-03-06
> **eduardoflsantos said:**
> 
I don't want to spend much money on this. 

Then why don't you try Bodhi Linux or similar as suggested in the other thread?

---

### Post by eduardoflsantos on 2014-03-06
> **mörgæs said:**
> Then why don't you try Bodhi Linux or similar as suggested in the other thread?

Well, in the other thread you said that SiS "has always been a problem and it's getting worse". So I assumed that I could have problems even with older releases, but that you think that I should try anyway, and Bodhi was a good one to start. If SiS is the problem, I prefer to remove it xD
That being said, I checked Bodhi, and it seems a great distro too, for my needs. I'll get it.

Bashing, I'll try to see the the identification numbers of the motherboard tomorrow.

I already have an external graphic card. Got it from my old PC (doesn't work anymore - dunno why) that have been stored in the attic for some years now xD. No idea which one it is, but the slots seems the same, I'll give it a try.

So, how can I disable that onboard damn SiS? :P

---

### Post by Bashing-om on 2014-03-07
eduardoflsantos; My morning to ya !

It has been my experience that if the card fits in the slot, and the monitor cable is correct for the connection, and a graphics driver is available: the card will work.
One should be able to enable that card's slot in bios ( something like enable pci ) which I expect will disable the onboard SIS graphics.

hey,
[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by eduardoflsantos on 2014-03-07
Hi there again,

So, I changed the graphic card, but I got into some trouble because PC reseted randomly, in the very start or when windows was loading.

I tried a few things, and ended up installing Bodhi. Now I can't remember if I installed it with the onboard graphic card or with the external one, but at the moment I'm running Bodhi with the external one. I'm liking it, although I never tried Lubuntu or Xubuntu that seems to fit for the same purpose. Let's see how I'll adapt to Bodhi, and if the system is solid enough :D

After inserting the external card, the onboard one stop sending image via VGA, so I switch the cable to the external one, and that was it, no need to do nothing special.

Not sure if this is thread is "solved", because I'll use Bodhi for now. Thank you both for yor help!

PS: Forgot to say. The system is SOOOO must fast now. I mean, this computer was replaced because even with Windows XP, it was impossible to work with, because it was very, very slow. Unworkable. Now, it's working just fine and it will be my PC at work :P

---

### Post by Bashing-om on 2014-03-07
eduardoflsantos; All right !

Yeah, if you are satisfied with Bodhi and that is to be the operating system ( hey, nothing wrong with Bodhi, it's linux too ); then yes, mark this thread solved.

We will move onto other things.

[INDENT][INDENT]see, it ain't nothing
[INDENT][INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

