---
title: "Ubuntu booting problem!"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by Bcrowes11 on 2011-04-01
I installed PLoP Boot Manager so I could boot from a usb flash drive. The problem is when I pick Install  Ubuntu to Hard Drive it hangs at "Loading casper/vmlinuz..."

Why? :confused:and How do I fix this? PLEASE HELP!!!:(

---

### Post by Dutch70 on 2011-04-01
You should probably select "Try Ubuntu" first to make sure it's going to run.

Have you tried selecting "check" when you get to the screen where you choose to Try of Install?

---

### Post by Hakunka-Matata on 2011-04-01
One way you can fix it is to reburn your usb stick using Unetbootin instead of PLOP.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Rubi1200 on 2011-04-01
Sounds like a problem with the way the image was put on the USB.

UNetbootin is an excellent recommendation.

---

### Post by Bcrowes11 on 2011-04-01
But I only have one usb drive and my mom's comp won't boot from usb without the help of plop...:(

---

### Post by Dutch70 on 2011-04-01
> **Bcrowes11 said:**
> But I only have one usb drive and my mom's comp won't boot from usb without the help of plop...:(

So did you check it, according to this...
[[COLOR="RoyalBlue"]Installation CD Integrity Check[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by Hedgehog1 on 2011-04-01
> **Bcrowes11 said:**
> But I only have one usb drive and my mom's comp won't boot from usb without the help of plop...:(

I find myself wondering - does your mom's computer have a CD drive?  If it doea you can boot using a LiveCD and do the 'TRY' and then 'Install' if things look good.

***The Hedge***

:KS

p.s. Your Mom is **OK** with you installing Ubuntu on her PC, right? :confused:

---

### Post by Bcrowes11 on 2011-04-01
Dodge70...would that be the same as check the memory?

Hedgehog...PLoP recognizes disk and says disk error.:(

---

### Post by Dutch70 on 2011-04-01
No, it's checking your usb even though it says cd, but if you're getting a disk error, that probably tell you what you need to know.

I've never used plop, but I would try completely clearing the disk & remaking it. 
**Check the md5sum of the downloaded .iso first.**
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by Bcrowes11 on 2011-04-02
I know how to check an md5sum. I did that. I had already loaded the distro on another computer. So I know it works. I can't clear the disk anyway because it's a cd-r. I just want to know why this thing won't load ubuntu...:(

---

### Post by Dutch70 on 2011-04-02
a cd-r :confused: I thought we were talking about a usb stick.

---

### Post by Bcrowes11 on 2011-04-03
Someone said to wipe the disk and reload it. This is not a cd-rw. I reloaded ubuntu on the usb drive more than once. If that's what you wanted to know.

ps...Hedgehog...My mom did give me the permission to do this...haha

---

### Post by Hakunka-Matata on 2011-04-04
dude, are you still using PLOP on that USB stick?  If so I reiterate, build the USB Install file using UNETBOOTIN and give it a try, sometimes, just doing it over 25million times works. 

Have you changed your socks? did that help?

---

### Post by Bcrowes11 on 2011-04-04
I understand what you mean finally. I tried installing ubuntu on the flash drive with unetbootin and now nothing'll even load in the screen with all the options. What is going on? Please help me guys!:(

---

### Post by Hedgehog1 on 2011-04-04
> **Bcrowes11 said:**
> ps...Hedgehog...My mom did give me the permission to do this...haha

Thanks for letting me know.  Now and then we get a *"I loaded Ubuntu on my Dads/Moms/Brothers/Sisters computer and it doesn't boot and I didn't have permission and they will be home in 20 minutes **HELP!!!**"* post.

I didn't want you in that painful place :P

Now about your issue: Not all USB sticks will boot.  They should, but some don't.

My I suggest you burn a CD from the ISO.  Do not create a CD that just has the ISO file on it - the ISO files is really a whole CD 'compressed' into a single file.  Use your CD burning software in the 'burn CD from ISO mode'.  The will uncompress the ISO during the burn and give you a complete, bootable CD.

Then boot off off that CD.  Report back when you have tried booting from the CD (as a note, if you do boot from the CD and you select 'TRY', you can get on the internet right from the CD and post here).

***The Hedge***

:KS

p.s. Hakunka-Matata: I changed my socks.  I don't think it helped the boot process, but I smell better. :P

---

### Post by Hakunka-Matata on 2011-04-05
[LIST]
[*]> **Bcrowes11 said:**
> I understand what you mean finally. I tried installing ubuntu on the flash drive with unetbootin and _**now nothing'll even load in the screen with all the options**_. What is going on? Please help me guys!:(
[/LIST]
 

[LIST]
[*]Do you mean that you get all the way to the screen where it's blue and you're presented with the choices of:
[LIST]
[*]Try Ubuntu without installing?
[*]Check disc
[*]Install Ubuntu?
[*]Imprecise representations of choices printed on screen, not verbatim i.e.
[*]Etcetera?
[/LIST]
 
[/LIST]



[LIST=1]
[*]If so, you may have not waited long enough after selecting your desired option and hitting THE ENTER Key,\
[*]Make your selection, Hit Enter, and go make a cuppa... chill,
[*]It sometimes takes a very long time, (in reality probably never had to wait more than a minute, but I have given up, gone off for a walk or something only to return to a nicely operating system).
[*] Bon Lucky...........
[/LIST]

---

### Post by Bcrowes11 on 2011-04-05
CD still not working...I'll try the flash drive and wait like hakuna suggested...time for :popcorn:

---

### Post by Bcrowes11 on 2011-04-06
I tried booting from the thumb...it didn't work. (shocker) So what's next?

---

### Post by Bcrowes11 on 2011-04-06
bump

---

### Post by Hakunka-Matata on 2011-04-08
> **Bcrowes11 said:**
> bump

Please supply thorough description of what the problem is.  

[LIST]
[*]What fails
[*]Where in the failing boot process does the machine choke?
[/LIST]

---

### Post by Hakunka-Matata on 2011-04-08
> **Bcrowes11 said:**
> bump

Please supply thorough description of what the problem is.  

I posted some command line stuff, but it is pre-mature, you need to get the OS installed first.  Are you attempting a 32 bit install?, or the .amd64 version?

---

### Post by Bcrowes11 on 2011-04-08
I boot from the usb. It loads vmlinuz. I says it's loading initrd.gz, but it'll hang there for hours and not do anything. It hangs at loading from the usb from any distro I've tried. I'm not running ubuntu...I'm running ***dows.

---

### Post by Bcrowes11 on 2011-04-08
I"m attempting a 32 bit instal.

---

### Post by Hakunka-Matata on 2011-04-08
What, you're installing in a Virtual machine?

---

### Post by Bcrowes11 on 2011-04-08
No...I'm attempting a complete erasing of windows. I want to Get rid of windows and replace it with ubuntu. At startup of the computer I choose to boot from usb. I get as far as "loading vmlinuz........
Loading initrd.gz........."
Then nothing ever happens. It stays there forever. 5 hours later it was still there. IT hadn't done anything.

---

### Post by LostFarmer on 2011-04-08
Your comp may be to old for Ubuntu,  give make/model, amount of ram , what MS windows is now installed, size of hdd.

---

### Post by Bcrowes11 on 2011-04-08
eMachines, 256 megs of ram, the processor is capable of ubuntu, I looked it up, it's like ten years old. XP Professional SP3.

---

### Post by Hakunka-Matata on 2011-04-08
> **Bcrowes11 said:**
> eMachines, 256 megs of ram, the processor is capable of ubuntu, I looked it up, it's like ten years old. XP Professional SP3.

256RAM may indeed be a problem, What kind of RAM does it require?

What follows applies to your setup with at LEAST 500MB RAM.

Me thinks  a good approach would be to massage the HDD first.

[LIST]
[*]The HDD has no data on it you care about, correct?
[*]If that is true, you can now attempt to format it, correct?
[*]I think your computer may be able to run Ubuntu Desktop.
[*]You need to get a USB stick with a basic OS on it, enough to run GParted.
[/LIST]
Who can help this guy get a bootable USB stick that has GParted ed on it?

I'll look myself, you'll get it going, nothing like positive energy to grease the gears.

---

### Post by Bcrowes11 on 2011-04-08
So you're gonna help me find the right distro?

---

### Post by Hakunka-Matata on 2011-04-08
Sure, any distro, they all work when you provide them with what they need to operate.  You know, like MINIMUM SYSTEM REQUIREMENTS.  YOU NEED SOME MORE RAM DUDE!

---

### Post by Dutch70 on 2011-04-08
I believe Lubuntu would be ideal. 
[[COLOR="RoyalBlue"]http://lubuntu.net/[/COLOR]]("http://lubuntu.net/")
[[COLOR="RoyalBlue"]http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Lubuntu-50492.shtml[/COLOR]]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Lubuntu-50492.shtml")
[[COLOR="RoyalBlue"]https://wiki.ubuntu.com/Lubuntu[/COLOR]]("https://wiki.ubuntu.com/Lubuntu")

You could always give Xubuntu a shot too. I think it runs better with 512mb of RAM though.
[[COLOR="RoyalBlue"]http://www.xubuntu.org/getubuntu[/COLOR]]("http://www.xubuntu.org/getubuntu")

---

### Post by Bcrowes11 on 2011-04-08
Well, I thought I had the min. requirements to run ubuntu. What do you need to know to help me now?

---

### Post by Bcrowes11 on 2011-04-08
Lubuntu hangs at "Loading initrd.lz........" WHY? I tried Slax, DSL, Ubuntu, Xubuntu, Lubuntu, WHY WON"T THEY WORK?

---

### Post by Hakunka-Matata on 2011-04-08
I quit.

---

### Post by Bcrowes11 on 2011-04-08
Please no! I need helpz!!!

---

### Post by debd on 2011-04-08
> One way you can fix it is to reburn your usb stick using Unetbootin instead of PLOP.


I used both.
made an bootable usb drive for installation with Unetbootin  ; then installed plop from windows. 
the 'disk2' in the plop boot menu(as far as I remember) took me in the Unetbootin drive's(usb) ubuntu menu.
**but remember, once U get ubuntu installed, do not install PLOP again as that would remove the grub mbr.**

---

### Post by Bcrowes11 on 2011-04-08
I've tried running Ubuntu by writing the unetbootin version, running it from PLoP. It did NOT work. I'm sorry. Does ANYone know what could be wrong?:(:confused:

---

### Post by debd on 2011-04-09
Bcrowes11,  you might want to see tis thread: [http://ubuntuforums.org/showthread.php?t=1710718](http://ubuntuforums.org/showthread.php?t=1710718)

---

### Post by Bcrowes11 on 2011-04-09
I tried that. I saw it yesterday, it didn't work.

---

### Post by Hakunka-Matata on 2011-04-11
OP, I already told you you most likely need more RAM.  Why don't you do what is suggested, or state plainly that you do not intend to buy and install more RAM.  
Tell me your intentions, and I will decide what to do next.  Most likely leave this thread because you are acting childish, or impertinent, or defensive, or just plain stubborn.  What will it be?

You know they say Ubuntu will run on almost anything, but the "anything" has to be some sort of computer that meets MINIMUM HARDWARE REQUIREMENTS.  Ubuntu for instance will not boot a bicycle, no matter how hard you try.

---

### Post by Bcrowes11 on 2011-04-11
But it DID meet minimum requirements. And no, I can't afford to get some more ram. Please don't take me as rude, or offensive. I'm not trying to be. I just need some help, please.

---

### Post by Dutch70 on 2011-04-11
[[COLOR="Red"]https://help.ubuntu.com/community/Installation/SystemRequirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by LostFarmer on 2011-04-11
The listed min. requirements is some what odd.  I am on Ubuntu and have only 512 M ram  Output of 'lshw'
 *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 512MiB

*-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz


I did not make any modifications during setup and used the normal install.  I'm not that smart.
Maybe I just lucked out.  I am just a simple user and not a gamer or other high resource user.

Bcrowes11:  You mention trying both a CD and USB flash drive, do both give same error ? 
1) you are using PloP on the hdd so you can select USB drive to boot.
2) you have UNETBOOTIN installed on the USB drive to boot linux.
 What is the menu entire on unetbootin for Ubuntu install? Post the complete menu entire. (Likely menu.lst, I have not used unetbootin)

using Plop on internial hdd ,  How ? web site link you used
installed unetbootin on usb drive , How ? web site link you used
 loaded ubuntu on the usb drive  , HOW ? web site link you used.
Make and Model on comp ?  give web site for its manual.
If I have time and you give me all links, will try to help . I will not try to find the links.

Run a memory test from MS Windows, before preceding.

Should try a different linux as link by [Dutch70]("http://ubuntuforums.org/member.php?u=595401") says your comp does not meet min. requirements and may be the problems

---

### Post by Dutch70 on 2011-04-11
> **LostFarmer said:**
> The listed min. requirements is some what odd.  I am on Ubuntu and have only 512 M ram  Output of 'lshw'
 
Should try a different linux as link by [Dutch70]("http://ubuntuforums.org/member.php?u=595401") says your comp does not meet min. requirements and may be the problems

Notice on that link it says, "recommended" minimum requirements, so you can run Ubuntu with less, it just won't run to it's full potential.
He's tried the lighter desktops & seems to have the same  problem. I still think he should stick with the a trying with a lighter desktop, because even if he gets Ubuntu installed, it will not be usable. 
*click on firefox, go make coffee
*click on a website, go take a shower
*click on email, go do your grocery shopping
*click on updates, go on vacation

Something like Puppy, or Macpup may be a better solution.

---

### Post by LostFarmer on 2011-04-11
Dutch70-- I will totally agree with you that a different linux might be a better pick. I do remember trying to boot Mepis 8.5 live cd , likely same requirements and it would not boot if it did not find my 2 swap partitions.  One swap was mounted I think selinux and the other swap. That will lead me to say Ubuntu will also need at least a swap if not 2, to load with the below memory requirements.   His comp may have more ram allotted to the display in the bios setup.

 I will try out the 2 linuxs that you listed. 

Just to say I have no problems with Ubuntu but I only use it for the net.

---

### Post by Bcrowes11 on 2011-04-11
ok, they changed it. I guess I have 256 mb of ram.

---

### Post by Dutch70 on 2011-04-11
[[COLOR="Blue"]Xubuntu System Requirements[/COLOR]]("http://www.xubuntu.org/get")
[[COLOR="Blue"]Lubuntu System Requirements[/COLOR]]("https://wiki.ubuntu.com/Lubuntu#System%20requirements")

I'd tell you more if I could, but that's about all I've got. :)

---

### Post by Bcrowes11 on 2011-04-11
thanks...I'll try this

---

### Post by Dutch70 on 2011-04-11
You may want to check this too.
[[COLOR="RoyalBlue"]https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall[/COLOR]]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall")

You may be surprised how nice Lubuntu is.

Just curious if you've ever been able to run a gparted live cd/usb. If so and you can get your hdd partitioned ahead of time. LostFarmer may be onto something with it using your swap partition as extra memory so to speak. Otherwise, you may just have to wait until you can buy more RAM like Hakunka said.

---

### Post by Bcrowes11 on 2011-04-12
lubuntu will not work. I'm getting a new used computer today or tomorrow, will try that.

---

### Post by Dutch70 on 2011-04-12
Great! If you can get it installed on the computer you're getting, then maybe you can move your hdd from the one you have to the one you're getting, install Lubuntu & move it back. Then you'll have 2 working systems.

---

### Post by Bcrowes11 on 2011-04-12
Sweet. I'll Try that, although you're gonna have to explain, or give me a demo on how to do that. I kinda don't know how to do so.

---

### Post by Hakunka-Matata on 2011-04-17
Bump

---

### Post by Bcrowes11 on 2011-04-17
Turns out I'm NOT getting that computer. I'm at a loss...BUMP:confused:

---

### Post by Dutch70 on 2011-04-17
Sorry to hear that. I can't remember all the details here, but check to make sure your usb stick doesn't have U3 software on it.
[http://psychocats.net/ubuntu/usb]("http://psychocats.net/ubuntu/usb")

Or, try a different usb stick.

---

### Post by Bcrowes11 on 2011-04-17
I think it's the computer, because I DID try another one.

---

