---
title: "ubuntu won't install"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by uberbuntufan64y on 2008-06-11
i tried to install ubuntu on my computer and it won't work! i've tried CDs and DVDs, i don't know what i'm doing wrong. i copied the ISO directly, downloaded it several times again to make sure it wasn't messed up or something. :confused:

EDIT: UPDATE:

I now get the installer to boot but I am still having trouble! Nothing seems to work! HELP!!!

---

### Post by avtolle on 2008-06-11
> **uberbuntufan64y said:**
> i tried to install ubuntu on my computer and it won't work! i've tried CDs and DVDs, i don't know what i'm doing wrong. i copied the ISO directly, downloaded it several times again to make sure it wasn't messed up or something. :confused:
Your problem, it appears to me, is that you are *copying* the iso, not burning it as an image. [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso) will give you some help.

---

### Post by uberbuntufan64y on 2008-06-11
i burned the iso.. i used up quite a few cds! :(

---

### Post by uberbuntufan64y on 2008-06-11
> **avtolle said:**
> Your problem, it appears to me, is that you are *copying* the iso, not burning it as an image. [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso) will give you some help.

i also looked at te site but the screenshots are too small to read :'(

---

### Post by avtolle on 2008-06-11
OK; did you do a checksum (md5sum) on the iso file after downloading it? The linked article discusses how to do this under windows. To see the screenshots in a larger format, click on the screenshot. 

Other "common" problems when doing this for the first time (believe me, I made a few coasters, too): burning at too high a speed (the slower, the better; I use 4x); using a CD-RW rather than a CD-R; using a "generic" rather than a "name brand" CD to burn to (Imation works for me). All these suggestions/pointers are given with a thought that your hardware may be mature, like mine, and the CD-ROM drive is a bit finicky.

Hope this helps.

---

### Post by uberbuntufan64y on 2008-06-11
i've also used nero burnig rom, roxiocd creator, and sonic burn... no luck ](*,)

---

### Post by uberbuntufan64y on 2008-06-11
> **avtolle said:**
> OK; did you do a checksum (md5sum) on the iso file after downloading it? The linked article discusses how to do this under windows. To see the screenshots in a larger format, click on the screenshot. 

Other "common" problems when doing this for the first time (believe me, I made a few coasters, too): burning at too high a speed (the slower, the better; I use 4x); using a CD-RW rather than a CD-R; using a "generic" rather than a "name brand" CD to burn to (Imation works for me). All these suggestions/pointers are given with a thought that your hardware may be mature, like mine, and the CD-ROM drive is a bit finicky.

Hope this helps.

i looked at how to do the md5sum and it seems confusing... but the izo file looks ok on the cd after i burn it on any computer i put it into and its the right file size and i've downloaded it a few times and they all are the same. ive tried imation, sony, tdk, and hp burnable cds!!! i have tried a lot of stuff already..

---

### Post by avtolle on 2008-06-11
Having violated the first rule of troubleshooting here, please respond to the following questions (that should have been asked first before getting into the other discussions):
1) Which release of Ubuntu are you trying to install, e.g., 8.04?
2) Are you trying the Live (Desktop) or alternate version?
3) What are your system specs, primarily processor name; the RAM in the box; video (graphics) card; and manufacturer of the PC?

Thanks for your anticipated response.

---

### Post by avtolle on 2008-06-11
And one more question (kicking myself repeatedly): is your boot order as set in BIOS such that your computer is to boot first from the CD drive?

---

### Post by uberbuntufan64y on 2008-06-11
i'm using hardy hardon, i've tried the live cd, the dvd image and the full set of cds... i stayed home from school today so i can get this working *lawls*


but i have tried lots of things and i keep thinking its going to work! :(

---

### Post by dje on 2008-06-11
does the live cd boot up to the desktop or not? do you get any errors, if you do please post them

dje

---

### Post by uberbuntufan64y on 2008-06-11
> **avtolle said:**
> And one more question (kicking myself repeatedly): is your boot order as set in BIOS such that your computer is to boot first from the CD drive?

i think so because i have installed ubuntu from a CD before just a few months ago, it took me forever to finally get it working but i did SOMETHING with the burning program.. i wish i could remember i think i'm doing it all the same! :confused:

 but my hard drive crashed and i had to get a new one and my old cd is scratched.

---

### Post by avtolle on 2008-06-11
@OP: I've got to get to work, not having the luxury of "staying home from school". So, while I'm leaving for now, I'll check back in when I can. Good luck.

@dje: Thank you for asking another question I should have asked when starting this discussion.

---

### Post by uberbuntufan64y on 2008-06-11
:mad:> **dje said:**
> does the live cd boot up to the desktop or not? do you get any errors, if you do please post them

dje

I don't get errors but the cds spin and the light blinks and there's a blinking cursor on the screen (i think it's trying to boot the CD) but then it just goes to boot up m$ windoze :mad:

---

### Post by dje on 2008-06-11
> **uberbuntufan64y said:**
> :mad:

I don't get errors but the cds spin and the light blinks and there's a blinking cursor on the screen (i think it's trying to boot the CD) but then it just goes to boot up m$ windoze :mad:

ok please post your computer specs
do you have more than one cd/dvd drive? if so have you tried both?

---

### Post by uberbuntufan64y on 2008-06-11
its a pentium 2, 333 megabite i think

i tried it in my brothers computer which is brand new and it still didn't work. it worked before a few months ago on his and my computer before i scratched the original CD that i had made... :(

---

### Post by uberbuntufan64y on 2008-06-11
i tried the burner and the cd-rom drive to boot the buntu cds and the same thing happens

(the disc spins, the green light blinks for about five to ten seconds, and then stupid windows boots up)

---

### Post by dje on 2008-06-11
i have to go now but try burning again following [these instructions]("https://help.ubuntu.com/community/BurningIsoHowto") with the program mentioned, then you can't go wrong ;)
I'll check back later to see how you got on, good luck!
Also are you using the same version as you tried last time? if not try using the same version (eg. 7.10 instead of 8.04)

---

### Post by uberbuntufan64y on 2008-06-11
> **dje said:**
> i have to go now but try burning again following [these instructions]("https://help.ubuntu.com/community/BurningIsoHowto") with the program mentioned, then you can't go wrong ;)
I'll check back later to see how you got on, good luck!
Also are you using the same version as you tried last time? if not try using the same version (eg. 7.10 instead of 8.04)

Thank you!! Thanks, I didn't burn the CD yet, but those instructions are soooo much easier than the first link I was sent!!!!!! I will try this and see if it works!@@@@ I'll be back
:guitar:

---

### Post by uberbuntufan64y on 2008-06-11
It Workeeeeeeeeeeeeed!!! I Have Been Trying For So Long I Was About To Get Pissed Hahaah But Its Working 8)

:-\"

Now to get it installed now that its booting.... I am using the hardy hardon liveCD now....!

---

### Post by avtolle on 2008-06-11
(Checking in): Good. Keep us posted, and best of luck.

---

### Post by uberbuntufan64y on 2008-06-11
...close but no cigar. the installer froze when i launched it from the live cd:mad:


.....

---

### Post by avtolle on 2008-06-11
System spec time, especially the amount of RAM in the box. If you have <384 mb RAM, I suggest using the alternate install CD as your hardware seems a bit "mature".

---

### Post by uberbuntufan64y on 2008-06-11
](*,)    :evil:


AAAAAAAAAAAAH IT NEVER ENDS!!!

---

### Post by avtolle on 2008-06-11
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) to get the alternate CD, check the box at the end of the description of the downloads that indicates alternate CD. 

I understand the frustration, but to use the HH "Live" CD, a minimum of 384 mb RAM is required. Since the installer is freezing, lack of RAM is, to me, the first thing to consider (I hope you checked the md5sum of the iso, too).

---

### Post by uberbuntufan64y on 2008-06-11
BUT AFTER ALL THIS WHY DOES IT HAVE TO FREEZE

....sigh

i guess i will try THAT one now.. it's practicly the only one i haven't downloaded i'm runing out of blank discs

---

### Post by avtolle on 2008-06-11
That is why I wanted your system specs earlier, to see if this might be avoided (if indeed, this is the problem). BTW, the alternate CD uses a text-based installer, which is to me quite intuitive, and will work in many situations where the Live CD won't.

---

### Post by dje on 2008-06-11
glad you got it to boot and good luck with the alternate cd :)

---

### Post by uberbuntufan64y on 2008-06-11
i REALLY hope this works this time., i'm running out of paitience

---

### Post by uberbuntufan64y on 2008-06-11
OK It is downloading right now... [-o<

---

### Post by uberbuntufan64y on 2008-06-11
Now it is downloaded, I HOPE THIS WORKS@!!!!!!:-#

---

### Post by uberbuntufan64y on 2008-06-11
where are all the graphics??????? this sux!!! :confused:

---

### Post by uberbuntufan64y on 2008-06-11
i thought i downloaded 8.04 but this all looks so old!

---

### Post by avtolle on 2008-06-11
As I posted earlier, this is text-based. No graphics. Just get it installed, and then see how it boots, etc. OK?

---

### Post by dje on 2008-06-11
it will install the same system but it is not a live cd because that takes a lot of ram, the alternate is just an installer for systems with less ram, you will end up with the same result ;)

edit: posted at the same time lol

---

### Post by DrinkWithRandall on 2008-06-11
You know ubuntu isn't really as user friendly as they tell you it is. My suggestion is to stay away from "Hardy Hardon" and use something else. Like Suse, Fedora, Slack anything that isn't Ubuntu.

---

### Post by WallyWest on 2008-06-11
> **DrinkWithRandall said:**
> You know ubuntu isn't really as user friendly as they tell you it is. My suggestion is to stay away from "Hardy Hardon" and use something else. Like Suse, Fedora, Slack anything that isn't Ubuntu.

Im surprised everyone keeps saying that. I pulled it right off the binary and installed it in fifteen minutes and had apache running perfectly in one day. Ive never even used a Linux OS before last week! Was that kid trying to dual boot or something? It would be easier if he just wrote over the whole partition.:confused:

---

### Post by dje on 2008-06-11
> **DrinkWithRandall said:**
> You know ubuntu isn't really as user friendly as they tell you it is. My suggestion is to stay away from "Hardy Hardon" and use something else. Like Suse, Fedora, Slack anything that isn't Ubuntu.

Not meaning to be horrible but since it's your first post here and you therefore haven't asked for help here saying ubuntu isn't user friendly isn't particularly justified, i'm sure if you had asked for help with your problems you would have had many replies and found a solution. Sorry but it just seems like pointless trolling especially as this is a support thread, but thats just my 2p

---

### Post by endre88 on 2008-06-11
Hello!

I've experienced the same problem for a long time. I tried to install several linux distros on my Asus A6Km laptop, and the installing procedure froze after a few seconds every time.
The solution was to turn ACPI off before starting the installation. In Ubuntu 8.04 desktop edition this can be done by hitting F6 on the welcome screen, and hitting ENTER on the ACPI off menu item, and hitting ESC, and starting the installation.

BTW: I have no luck with this destro either, 'cause I've installed it, but it freezes after trying to boot it.

Hope I could help.

---

### Post by avtolle on 2008-06-11
> **endre88 said:**
> Hello!

I've experienced the same problem for a long time. I tried to install several linux distros on my Asus A6Km laptop, and the installing procedure froze after a few seconds every time.
The solution was to turn ACPI off before starting the installation. In Ubuntu 8.04 desktop edition this can be done by hitting F6 on the welcome screen, and hitting ENTER on the ACPI off menu item, and hitting ESC, and starting the installation.

BTW: I have no luck with this destro either, 'cause I've installed it, but it freezes after trying to boot it.

Hope I could help.
You need to do the same thing as a boot parameter when you boot it; I believe is is noacpi, added to the end of the boot line (believe this is F6, too, someone check me on this). That should let you boot.

---

### Post by dje on 2008-06-11
> **avtolle said:**
> You need to do the same thing as a boot parameter when you boot it; I believe is is noacpi, added to the end of the boot line (believe this is F6, too, someone check me on this). That should let you boot.

yes add it to /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```
then add the noapic option to the end of the boot options, then it will stick after every reboot. for example:
```
kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=e2065b85-e213-4129-bf6f-ecbb89165c8d ro quiet splash **noapic**
```

hope that helps,
dje

---

### Post by uberbuntufan64y on 2008-06-11
i remember that it worked last time without having to do any of this! i'm so confused!:mad:

should i try another distro? or older version? :confused:

---

### Post by avtolle on 2008-06-11
Ignore the posts about noapci; they don't apply to you. Have you been able to finish installation of 8.04?

---

### Post by endre88 on 2008-06-11
```
kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=e2065b85-e213-4129-bf6f-ecbb89165c8d ro quiet splash **noapic**
```


Thanks for the quick reply! Actually, the proper add-on is **acpi=off**.

---

### Post by avtolle on 2008-06-11
> **endre88 said:**
> ```
kernel    /boot/vmlinuz-2.6.24-19-generic root=UUID=e2065b85-e213-4129-bf6f-ecbb89165c8d ro quiet splash **noapic**
```
Thanks for the quick reply! Actually, the proper add-on is **acpi=off**.
That's why I asked someone to check me; can't trust my memory. :-)

@OP: How is it coming along?

---

### Post by endre88 on 2008-06-12
@OP: How is it coming along?[/QUOTE]

Now everything is fine with this distro! The graphical effects and the quickness is just stunnig! :D

---

### Post by awahid2020 on 2008-06-12
WINDOWS XP NEEDS MORE USER INFORMATION IN SETUP AS COMPARED TO UBUNTU.

Just Pop in the UBUNtu CD, reboot ur machince, just check the boot order, machine boots from cd, install UBUNTU, that's all. 
Select partition for hard disk where u want to install it, and let the WIZARD do the filesystem format thing, I DID THIS WAY, IN DUAL BOOT and SINGLE HARD DISK, and its working
HE HE HE

---

### Post by uberbuntufan64y on 2008-06-12
it's still looks all crummy with text and stuff... :confused:

how do i get the graphics back???:mad:

---

### Post by uberbuntufan64y on 2008-06-12
i'm about to give up :(

---

### Post by uberbuntufan64y on 2008-06-12
should i try a boot parameter like that guy had to or something? i've tried so many things already... i need to get this working i'm obsessing over getting it to work!!!

---

### Post by DrinkWithRandall on 2008-06-12
> **dje said:**
> Not meaning to be horrible but since it's your first post here and you therefore haven't asked for help here saying ubuntu isn't user friendly isn't particularly justified, i'm sure if you had asked for help with your problems you would have had many replies and found a solution. Sorry but it just seems like pointless trolling especially as this is a support thread, but thats just my 2p

Hello,

I don't need any help. I'm vary familiar with linux and can google for a answer if needed. But I am helping people in linux. Just because you don't agree with my answer you don't have to shoot me down. is it not your philosophy to help people with "linux"? So next time before you put your 2 "Cents" in be a little nicer.

---

### Post by uberbuntufan64y on 2008-06-12
> **awahid2020 said:**
> WINDOWS XP NEEDS MORE USER INFORMATION IN SETUP AS COMPARED TO UBUNTU.

Just Pop in the UBUNtu CD, reboot ur machince, just check the boot order, machine boots from cd, install UBUNTU, that's all. 
Select partition for hard disk where u want to install it, and let the WIZARD do the filesystem format thing, I DID THIS WAY, IN DUAL BOOT and SINGLE HARD DISK, and its working
HE HE HE



i got it to load now but it's old looking and crappy... i don't know whats wrong with the installer! i've never seen anything like this ](*,)

---

### Post by avtolle on 2008-06-12
What is "old-looking and crappy"? Really, you need to be more specific. 

Did you get 8.04 installed from the alternate CD? Are you still trying to install? Just where are you in the process?

---

### Post by decoherence on 2008-06-12
Please read what people post and worry less about giving us a play-by-play.

The alternate installer looks old and crappy. That's why it's the 'alternate.' It is meant to install on old machines like yours. It will install the same system as the graphical installer. This has been said several times in the thread.

Good luck,

---

### Post by uberbuntufan64y on 2008-06-12
i'm in the installer but my mouse isn't working :(

---

### Post by avtolle on 2008-06-12
> **uberbuntufan64y said:**
> i'm in the installer but my mouse isn't working :(
Can you move around using the "arrow" keys or by hitting the Tab button to move the highligh to what you want to select and then hitting Enter (or Return, depending upon your keyboard) to actually select it? If so, do this isntead.

---

### Post by uberbuntufan64y on 2008-06-12
i recently upgraded to a new usb mouse and keyboard could this be the problem that is happening? i think i threw out my old ones that were a round plug instead. (one was green and the other was purple).

---

### Post by uberbuntufan64y on 2008-06-12
> **decoherence said:**
> Please read what people post and worry less about giving us a play-by-play.

i have been reading! i appreciate the help too.... really! i'mm just really frustrated... :(

> Can you move around using the "arrow" keys or by hitting the Tab button to move the highligh to what you want to select and then hitting Enter (or Return, depending upon your keyboard) to actually select it? If so, do this isntead. 

i tried to tab and press the arrow keys and... they don't work :( 

maybe the NUM lock is the problem? but i tried pressing that too and still the arrows aren't working...

---

### Post by uberbuntufan64y on 2008-06-12
i just tried it on my brothers computer and the keyboard works on his in the installer, but i didn't keep going on with the installation obviously. i wonder if there is a problem with my computer! but the keyboard and mouse work fine with the LIVE CD

begin venting frustration: AWER#@(MFP(R MOWFMKWAP$OMRACE P(OT)(#IRP(OJFEAFJAEWFMMEFEWA:mad::mad::mad:](*,):-k:evil:#-o:x
ewarfEWAR@A#R
ewrar32420jofpfwaimnpoewaijfopaj4fp30jfpfwoeajfpa  aAW#$VQ#RB$^HGVG @$$
end venting frustration

EDIT: what could i possibly try now? IVE TRIED EVERYTHING!!!

---

### Post by uberbuntufan64y on 2008-06-12
maybe i should try 7.10 version? i think thats what i used last time and it worked... is there any reason why i shouldn't? but i don't want to downgrade.... blaaaaaaaaaaaah

---

### Post by avtolle on 2008-06-12
This whole adventure began with you stating that while your system ran from the Live CD, the installer hung. Thus, the suggestion to try the alternate CD.

Your brother's computer is newer, as I recall. The fact that the keyboard works on his under the installer and your replacement keyboard and mouse in your older system do not only means that there is some reason the usb keyboard and mouse you upgraded to is not being recognized by the installer (I've a feeling that's why the Live CD installer "hanged" as well). Did the new accessories work under whatever OS you had on the box before beginning the attempted installation of Ubuntu?
I've a feeling that this may be a BIOS problem, but as I am not sure, don't do anything with the BIOS on your computer at this point. I think the installer is looking for a PS/2 keyboard and mouse as that is being reported to it by the BIOS as being there, and, obviously, the same aren't there any more. 

So, in an attempt to get things moving, is there any way you can get a PS/2 keyboard and a PS/2 mouse to use to complete the installation? Or, do you have a USB/PS/2 converter piece around that you could use to plug your USB keyboard into a PS/2 slot, for example, to get the installation completed?

---

### Post by DrinkWithRandall on 2008-06-12
> **uberbuntufan64y said:**
> maybe i should try 7.10 version? i think thats what i used last time and it worked... is there any reason why i shouldn't? but i don't want to downgrade.... blaaaaaaaaaaaah


I can understand you frustration you are installing ubuntu and this can be real pain in the ***. My suggestion is to download Fedora and give that a try. you can download fedora at [http://fedoraproject.org/](http://fedoraproject.org/) download the installer dvd. Once you download the iso you can use a burning program to burn the iso to disk. 

I know no one on here told you what the iso is so I will explain for you. An ISO file is a file that can contain a image of a cd/dvd. you have to use a program to burn that image to disk. You Have roxio you can use roxios burn from image file to do that. 

Once you have that downloaded an burned you can boot it off the dvd. Once the Fedora Boot menu comes up you can select text installer option. Use your arrow keys and the enter key to make your selections. continue on till you get to Package Selection when you see this use your arrow keys and select the customize software selection and hit the space bar. then use your arrow keys to go down to ok hit enter. go all the way down till you see XFCE when you have selected that hit space. Then arrow down to ok then hit enter. this will start the install process. This should work for you let me know how it turns out.

---

### Post by uberbuntufan64y on 2008-06-12
> **avtolle said:**
> So, in an attempt to get things moving, is there any way you can get a PS/2 keyboard and a PS/2 mouse to use to complete the installation? Or, do you have a USB/PS/2 converter piece around that you could use to plug your USB keyboard into a PS/2 slot, for example, to get the installation completed?

I threw out my old keyboard/mouse... I don't have any spares :(

---

### Post by uberbuntufan64y on 2008-06-12
> **avtolle said:**
> Your brother's computer is newer, as I recall. The fact that the keyboard works on his under the installer and your replacement keyboard and mouse in your older system do not only means that there is some reason the usb keyboard and mouse you upgraded to is not being recognized by the installer (I've a feeling that's why the Live CD installer "hanged" as well). Did the new accessories work under whatever OS you had on the box before beginning the attempted installation of Ubuntu?
I've a feeling that this may be a BIOS problem, but as I am not sure, don't do anything with the BIOS on your computer at this point. I think the installer is looking for a PS/2 keyboard and mouse as that is being reported to it by the BIOS as being there, and, obviously, the same aren't there any more.

The keyboard and mouse were working on the LiveCD until I tried to launch the installer then everything froze :(

---

### Post by uberbuntufan64y on 2008-06-12
> **DrinkWithRandall said:**
> I can understand you frustration you are installing ubuntu and this can be real pain in the ***. My suggestion is to download Fedora and give that a try. you can download fedora at [http://fedoraproject.org/](http://fedoraproject.org/) download the installer dvd. Once you download the iso you can use a burning program to burn the iso to disk. 

I know no one on here told you what the iso is so I will explain for you. An ISO file is a file that can contain a image of a cd/dvd. you have to use a program to burn that image to disk. You Have roxio you can use roxios burn from image file to do that. 

Once you have that downloaded an burned you can boot it off the dvd. Once the Fedora Boot menu comes up you can select text installer option. Use your arrow keys and the enter key to make your selections. continue on till you get to Package Selection when you see this use your arrow keys and select the customize software selection and hit the space bar. then use your arrow keys to go down to ok hit enter. go all the way down till you see XFCE when you have selected that hit space. Then arrow down to ok then hit enter. this will start the install process. This should work for you let me know how it turns out.

I might try fedora because UBUNTU ISNT WORKING!!!!!!!!!! :evil:

---

### Post by avtolle on 2008-06-12
I understand that the keyboard and mouse were working under the Live CD until you tried to launch the installer. Looks like the installer (whether under the Live CD or the Alternate CD) is not recognizing the new usb keyboard and mouse, as I posted before. Until that can get resolved, I'm of the opinion that you're not going to get 8.04 installed. So, presuming that:

a) Get a good cd of the 7.10 iso (whichever one you want) and try to install that, and perhaps if it installs and everything works well, do a distribution upgrade through upgrade manager to 8.04;

b) Try Fedora or OpenSuse or some other distro.

---

### Post by uberbuntufan64y on 2008-06-12
> **avtolle said:**
> I understand that the keyboard and mouse were working under the Live CD until you tried to launch the installer. Looks like the installer (whether under the Live CD or the Alternate CD) is not recognizing the new usb keyboard and mouse, as I posted before. Until that can get resolved, I'm of the opinion that you're not going to get 8.04 installed. So, presuming that:

a) Get a good cd of the 7.10 iso (whichever one you want) and try to install that, and perhaps if it installs and everything works well, do a distribution upgrade through upgrade manager to 8.04;

b) Try Fedora or OpenSuse or some other distro.

I think I will try the 7.10 versions, guess I have ANOTHER download and burn to do... SIGH :mad:

I REALLY DONT WANT TO HAVE TO SWITCH TO ANOTHER DISTRO BECAUSE I USED UBUNTU BEFORE ON THIS COMPUTER!!!!!!! IT SHOULD WORK ahhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

---

### Post by dje on 2008-06-12
> **DrinkWithRandall said:**
> Hello,

I don't need any help. I'm vary familiar with linux and can google for a answer if needed. But I am helping people in linux. Just because you don't agree with my answer you don't have to shoot me down. is it not your philosophy to help people with "linux"? So next time before you put your 2 "Cents" in be a little nicer.

Hi

Well you were putting your point across and i was putting mine across (i think ubuntu is a wonderful, easy to use and user friendly distro). it just appeared, to me, that you had come to the ubuntu forums to put rip ubuntu. i was not putting down the idea to try other distros, i think that the OP should if ubuntu does not work for him and it is certainly a valid idea. i was not meaning to be horrible, if the post came across that way i apologise

dje

@OP if 7.10 was what worked, try one last download and see if it works, remember the alternate may look crappy and you can't use the mouse but you end up with the same result ;)

---

### Post by cmnorton on 2008-06-12
> **uberbuntufan64y said:**
> i tried to install ubuntu on my computer and it won't work! i've tried CDs and DVDs, i don't know what i'm doing wrong. i copied the ISO directly, downloaded it several times again to make sure it wasn't messed up or something. :confused:

EDIT: UPDATE:

I now get the installer to boot but I am still having trouble! Nothing seems to work! HELP!!!

1) I know it is possible to download CD/DVD images directly from the internet, but I seem always to have bad luck doing it. That is, the images I burn are no good. On Windows and Linux I use bittorrent; it's free; and you just need to search for Ubuntu bittorrents, instead of ISO images. 

The torrent's file name gives you an idea of the distribution you would download, like Kubuntu or Ubuntu, and even the type of installer is included in the title, like for the alternate mode installer.

2) Even Ubuntu 6.10's "regular" installation never liked my Acer laptop with its nvidia chip. I had to use the alt-mode install on that, so now I just go ahead and use the alternate mode install, and download and burn the iso image from the appropriate torrent.

3) Try to locate a PS/2 keyboard and mouse, or borrow them from a friend. They are useful to have around. 

4) I understand one person replying to your original post was offering you alternatives to Ubuntu. It did not sound to me like this was bashing, but instead was offering you a way out of your troubles. 

Please note however if you cannot successfully burn a Fedora CD, you will still have problems.

---

### Post by cmnorton on 2008-06-12
> **WallyWest said:**
> Im surprised everyone keeps saying that. 

We keep saying "that", because there have been genuine install/upgrade problems with the 8.04 release. I had the luxury of trying upgrades and full installs, and they went badly using a PIV older laptop and a brand new Thinkpad T61p hardware. The older laptop has 1GB RAM; the newer laptop 2GB RAM. 

In all fairness however, I had converted one of my older PIV desktops that upgraded 6.10 to 7.04 to 7.10 flawlessly to RH EL 4, so I was not able to try the 8.04 upgrade on that system.

I enjoy using Ubuntu and Kubuntu, and look forward to trying the 8.04.1 release, which should be in a few weeks.

---

### Post by uberbuntufan64y on 2008-06-12
:confused:> **dje said:**
> 

@OP if 7.10 was what worked, try one last download and see if it works, remember the alternate may look crappy and you can't use the mouse but you end up with the same result ;)


ubuntu 7.10 *also... *doesn't... work...

i also asked some friends if they have old keyboards... no luck on that......

maybe i'm doomed not to use ubuntu.......

---

### Post by uberbuntufan64y on 2008-06-12
Noooooooooooooooooooooooooooooooooooooooooooooooooo!

---

### Post by uberbuntufan64y on 2008-07-04
ok, it still not working...


](*,):sad::sad::sad:

i really wish i could get this to work:confused:

---

### Post by uberbuntufan64y on 2008-07-04
someone PLZ helperz.............:(

---

