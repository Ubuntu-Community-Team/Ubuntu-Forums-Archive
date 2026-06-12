---
title: "GRUB loading 1.5. Error 22 - how to get rid of GRUB?"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by farzel on 2008-04-18
Hello
I'm a very unexperienced beginner in LINUX and I just manage to install it. I made the error to install Kubuntu on a Laptop where there was already Windows and in both OS the computer became very slow. Now I need to cut a video and therefor I wanted to desinstall the Kubuntu and I did it in a very easy but stupid way: I deleted the partitions with a programm that I used in Windows. When i restarted the laptop tells me:

GRUB loading 1.5. Error 22

... and than I don't get to windows and nothing....
So I wanted to ask if somebody can tell me in easy steps what to do to uninstall the GRUB and make the laptop simply start in windows?
I'm sorry to ask something here that will make me work in windows, if I would be expert enough I would kick all this windows **** and take a linux programm for cutting videos but I don't really know if there is one and if this will work with the formats etc.
nfortunately I need now the short solution and get back to windows. after cutting this video I will try it with Kubuntu only... I promise :)

---

### Post by olskar on 2008-04-18
This will at least get windows back for you:
[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

---

### Post by eyesonly2003 on 2008-04-20
I think deleting the Ubuntu files makes perfect sense because when you put in the Ubuntu CD it doesn't have a menu entry for Uninstalling the operating system.

Your first instinct after not being able to uninstall it is to just 'delete this rubbish'. :idea:

I tried Ubuntu on another machine on it's 2nd hard drive. I downloaded the Nvidia 6800xt Linux driver which was suchandsuch.run. I set priveleges and on and on and I tried trying to install the .run package to update the video card drivers for far too long and said this is retarded. How hard does it have to be to install a driver?! ](*,) It just doesn't run in terminal, and why because it has to be run as root?!? what the root is root?! So I go to unisnstall it and you can't, so I deleted it and I have a grub error. What the hell is a grub?!:confused:

Windows is way ahead of this insanity! I wanted an OS on my old machine to maybe sell it because I am using my XP Pro SP2 on my new machine I built. I wouldn't wish Linux on anyone. I have bought a Windows XP home that I will put on it because Windows XP just works!!!! I used to develope for mac and windows and I didn't know you could make something worse than Mac yet here we are. 

YOU GET WHAT YOU PAY FOR; 
FREE IS TOO MUCH TO PAY FOR LINUX!! :rolleyes:

Dare I try PCLOS =;

---

### Post by TheExplorer on 2008-04-20
Rather foolish and a bit unkind. Sad...
Grub is just a loader like ntloader in Windoze. When you install linux over M$ you have to pay a bit of your attention to where you install your OS loader. Googling this out will not hurt you.
 So, it's rather predictable if you just delete linux partitions from M$ not having restored your MBR first... Let me ask you a question: how did you simply manage to "develope for mac and windows"? :)
 I won't tell you how to restore MBR in M$ intentionally 'cause the answer is just "on the surface" over the net.
> because Windows XP just works!!!!
and
> How hard does it have to be to install a driver?!
That just depends on the "straightness of your hands". It takes just one line of code in the terminal to install it.

In the end I would like to disappoint you - Linux just works :)

---

### Post by farzel on 2008-04-21
thanks for the ones that gave constructive feedback.
the solution that was proposed in that external link sounds easy, even for me, but I have one problem: I don't have the windows CD anymore... as I anyhow only want to use it for cutting a film that I need urgently and than switch to Linux....
so what I would need is another solution....
not so easy...

---

### Post by zvacet on 2008-04-21
Reinstall [grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") or try to restore it with [Supergrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

---

