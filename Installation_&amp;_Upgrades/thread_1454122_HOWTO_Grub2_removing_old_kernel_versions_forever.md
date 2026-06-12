---
title: "HOWTO: Grub2 removing old kernel versions forever"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Unknown Hero on 2010-04-14
Hello!

I was looking for this for quite some time today and I didn't find anything. At the end, I managed to solve the problem myself.
Here's how to always have only the latest kernel version in your grub:
```
sudo gedit /etc/grub.d/10_linux
```
Find these lines:
```
list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
```
and change it with this:
```
for ver in /boot/vmlinu[xz]-* ; do
  list="$ver"
done
```
Notice two differences.
1. There's no ` before "for" and after "done" keywords.
2. There's no list= before "for"

If you want to change the name of entry, scroll down to the end of the file and find last two occurrences of:
```
linux_entry
```
${OS} stands for Ubuntu and ${version} stands for your kernel version. I changed this into:
```
  linux_entry "${OS} 9.10 Karmic Koala" \
```
You can use your own imagination.
If you want to have specific name for your Windows entry, in /boot/grub/grub.cfg copy everything between:
```
### BEGIN /etc/grub.d/30_os-prober ###
```
and
```
### END /etc/grub.d/30_os-prober ###
```
paste it in
/etc/grub.d/40_custom
change the text between double quotes right after menuentry
(For example, my 40_custom looks like this now:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set bcdc24dddc249424
	chainloader +1
}
```
)
and make 30_os-prober not executable:
```
sudo chmod -x 30_os-prober
```

If you want to remove recovery mode entry, just uncomment this line in /etc/default/grub:
```
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

PS Don't forget to run ```
sudo update-grub
``` after you finish editing everything! And check in /boot/grub/grub.cfg if everything is ok!

Post any questions if you have.

Cheers!

---

### Post by zvacet on 2010-04-14
Easier and practical (because if kernels doesn´t show in grub they are still installed and they take some place on your HD)way to do the same is to remove kernels using synaptic.In synaptic search box type linux-image and you will find all installed kernels.Remove all except one with higher number.Do this when you test latest kernel and you are sure that it works how it should.For that reason it is good idea to have two kernels.Of course in this case also you will,after removing kernels with synaptic run in terminal


```
sudo update-grub
```

---

### Post by Unknown Hero on 2010-04-17
Actually Synaptic runs ```
sudo update-grub
``` by itself after you remove old kernel versions.

My solution is supposed to be one solution forever. You do this only once and it's working forever.
In case newest kernel version doesn't work well, you can always boot with live CD and make older kernel versions possible to choose during booting.

---

### Post by ScripterJR on 2010-04-28
Unknown Hero, I'm new to this whole Linux/Ubuntu stuff so excuse me if I don't understand much. You're solution works exactly how I wanted it to. Only thing I couldn't find though from the internet is if I would want to make 30_os-proper executable what would I need to type in the terminal. Also, you don't mention anything about MemoryTestx86+, should that stay in the menu entry?

also when doing:
```
sudo chmod -x 30_os-prober
```

I get:
```
chmod: cannot access '30_os-prober': no such file or directory
```

---

### Post by ice333 on 2010-04-28
Just wondering why so many folks want to spend time typing so many lines of unintuitive gibberish into a terminal when all that is needed to remove old kernels completely is a simple click of the mouse in an app like Ubuntu Tweak????:lolflag:

---

### Post by The Thunder Chimp on 2010-04-29
> **ice333 said:**
> Just wondering why so many folks want to spend time typing so many lines of unintuitive gibberish into a terminal when all that is needed to remove old kernels completely is a simple click of the mouse in an app like Ubuntu Tweak????:lolflag:

Look ice33, continue using Ubuntu for about 3-4 months, and you'll be on our side. The command line is ten times as fast to execute commands, and has a larger range of capabilites. And "unintuitive" might be unintuitive but it's definetly something you can learn...It's not much harder to use the command line than to get around a maze of clicks...

By the way, welcome to the Community!

---

### Post by MattTastic on 2010-04-29
> **The Thunder Chimp said:**
> Look ice33, continue using Ubuntu for about 3-4 months, and you'll be on our side. The command line is ten times as fast to execute commands, and has a larger range of capabilites. And "unintuitive" might be unintuitive but it's definetly something you can learn...It's not much harder to use the command line than to get around a maze of clicks...

By the way, welcome to the Community!

Cut the guy some slack will you. I presume everyone here would like it one day that Microsoft/Apple weren't the dominant players in software/OS and the only way for that to happen is the average Joe getting on the GNU bandwagon. But that won't happen if they have to change their behaviour. I'm an avid terminal user myself but I do realise the important of GUIs for the average entry level user.

---

### Post by ice333 on 2010-04-29
Some good points made by both of you guys, yes I'm sure the CLI is a very capable tool and I have no doubt that many things could not be done without it and I am more than happy to learn it and in fact have been doing so as, **so far, I really love Linux** (running Mint 8 in dual boot with Vista but have Ubuntu 9.10 in VirtualBox within Mint host).

I havent booted into windows for many weeks now.

But for goodness sake guys, even a total newbie like me can see in the above posts the absurd lengths some folks will go to to avoid clicking on a mouse, I mean do people really break out with an allergy to using a mouse??. I refer to doing a straightforward removal of an old/previous Kernel version (which so far I have done twice with perfect success), why would anyone want to type so much stuff having to be so careful as they do so, like above steps explained, when in a really good program like Ubuntu Tweak, you click on a button and it takes care of everything beautifully, at most there are 3 clicks involved, hardly a 'maze of clicks'.

The only conclusion I can come to upon this observation is perhaps some people think that it is in some way a really super-clever thing to do (loads of commands vs. 3 clicks), personally I think it's in many ways going back to retro computing like the guys wearing white jackets in a large room with a large mainframe in the 1970's, when there was no choice but to enter a load of gibberish into a boring terminal. Since then the GUI has been invented and has progressed a long way imho.

So do forgive my above laughter, it's not actually meant in a bad way but looking above it's damn well appropriate.......................ohhhh, lets all go back to the 1970's, use a monochrome terminal, put on some white jackets and grow beards!!!:lolflag::lolflag::lolflag::lolflag:

---

### Post by The Thunder Chimp on 2010-04-29
> **MattTastic said:**
> Cut the guy some slack will you. I presume everyone here would like it one day that Microsoft/Apple weren't the dominant players in software/OS and the only way for that to happen is the average Joe getting on the GNU bandwagon. But that won't happen if they have to change their behaviour. I'm an avid terminal user myself but I do realise the important of GUIs for the average entry level user.
 
Calm down man, I never said anything agressive. I like to use the mouse too. Simply, the CLI can do much more than the GUI, overall.
 
 And talking about hard it is to enter things in a terminal without making any mistakes, a simple copy-paste does the trick ;)

---

### Post by Unknown Hero on 2010-05-05
> **ScripterJR said:**
> Unknown Hero, I'm new to this whole Linux/Ubuntu stuff so excuse me if I don't understand much. You're solution works exactly how I wanted it to. Only thing I couldn't find though from the internet is if I would want to make 30_os-proper executable what would I need to type in the terminal. Also, you don't mention anything about MemoryTestx86+, should that stay in the menu entry?

also when doing:
```
sudo chmod -x 30_os-prober
```

I get:
```
chmod: cannot access '30_os-prober': no such file or directory
```

You obviously don't have file called 30_os-prober. Type ```
ls
``` and find xx_os-prober (where xx is some number) and run the same command for that file.

---

### Post by wilee-nilee on 2010-05-05
```
sudo apt-get autoremove
```

---

### Post by jicampbell on 2010-05-07
> **ScripterJR said:**
> Unknown Hero, I'm new to this whole Linux/Ubuntu stuff so excuse me if I don't understand much. You're solution works exactly how I wanted it to. Only thing I couldn't find though from the internet is if I would want to make 30_os-proper executable what would I need to type in the terminal. Also, you don't mention anything about MemoryTestx86+, should that stay in the menu entry?

also when doing:
```
sudo chmod -x 30_os-prober
```I get:
```
chmod: cannot access '30_os-prober': no such file or directory
```

This has also probably been solved, but just in case anyone is stumbling across this thread (like I did), I used:

```
cd /etc/grub.d/
```

to set the directory and then the chmod worked fine. I'm ridculously new to Ubuntu (as in last friday! Genuinely loving it. Came along at quite an inopportune time though... last exam of first year at Uni on Wednesday... :P) but that seems an easyish thing to do to stop yourself getting an error.

---

### Post by ronparent on 2010-05-07
This seems all to be much ado about if not nothing, very little. Fooling around a couple of weeks ago I selected 'clean' from the recovery mode menu. Lo and behold, all my old kernels disappeared forever whether I wanted them to or not. I had to run update-grub to get the old kernels out of the grub boot menu. If that is what you want, that is what you end up with.:lolflag:

---

### Post by dndrich on 2010-05-10
> **ice333 said:**
> Just wondering why so many folks want to spend time typing so many lines of unintuitive gibberish into a terminal when all that is needed to remove old kernels completely is a simple click of the mouse in an app like Ubuntu Tweak????:lolflag:

I have Ubuntu Tweak, and I do not see that entry. I have a bunch of old kernels apparently in my list, but I can't get rid of them. I have searched in synaptic, and they don't seem to exist!

---

### Post by mailc on 2010-06-12
> **dndrich said:**
>  I have a bunch of old kernels apparently in my list, but I can't get rid of them. I have searched in synaptic, and they don't seem to exist!
 In Synaptic search for ' 2.6.32 ' .  Another digit will be at the end  - be careful not to remove the latest (highest number ).  Let us know

---

### Post by ice333 on 2010-06-14
> **dndrich said:**
> I have Ubuntu Tweak, and I do not see that entry. I have a bunch of old kernels apparently in my list, but I can't get rid of them. I have searched in synaptic, and they don't seem to exist! 
Click on "package cleaner" on the top left of the list on the left side of the program window, then you will see the buttons labeled "clean package", "clean cache", "clean config", "clean kernels"............then one click and you're done :popcorn:

---

### Post by Moozillaaa on 2011-02-05
Alright there Hero; if I'm reading correctly, then I can chainload from my first GRUB2 -> second GRUB2 , by editing 40_custom file, with the entry for GRUB2 .img ???

Like so:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "GRUB2 on Disk 2" {
         root (hdX,Y)
         kernel /boot/grub/core.img
         boot
	
}
and then make 30_OS prober like so???
> 
and make 30_os-prober not executable:

Thanks here...

---

### Post by cojon on 2011-03-13
May I make a comment as to CLI and GUI? 

Why do we need to have dual sides with actions close to fighting? 

I fully agree, the command line has incredible benefits. In one way, it is (depending on your accurate memory and typing speed) faster to use than a GUI. Additionally, looking at this situation as a behavioral psychologist with a Ph.D. and more years of training than you have with Linux, I see something else. To save a few apparently arrogant CLI users some real embarrassment however, I will refrain from mentioning it.    

Consider further if you will, and show off your intelligence as well as your years of memorizing. As some who have posted here have done well, consider the benefits of both CLI and GUI. I think you will find that the CLI is for those who use it well, and the GUI is for those of us that prefer it. If you manage an IT system, I would think you might enjoy CLI--because it shows off your abilities to those who may care. Then you may continue to learn and boast.  

Those who use the command line have paid some real memory intensive dues, or they have a naturally excellent memory. Not everyone can or cares to do this. Additionally, there are those who cannot type like robots, with blurred fingers flying as commands are entered faster then spent shells out of a tommy gun. I am one of them. 45 wpm is my three finger limit, and I feel great at it. No, I can't show off, but I feel no need to. many of the GUI people feel similarly. Comfortable with a mouse, they are not looking for praise or rejection, just doing what must be done. Those who are like the cars that race about town at a dangerous 60 MPH, but arrive at the stoplight a mere twelve seconds earlier than Grandma Moses who, listening to the 20's tunes, doesn't seem to care and fully enjoys her 1934 Oldsmobile, should take a bit of notice and realize that differences do not make enemies, anger does, and it's really unnecessary.  

There is a place for everyone. 

Consider this . . . I have seen in print here a desire to have Ubuntu Linux overtake Microsoft. As a psychologist who has spent many years as a business consultant (now retired) I can assure you that is quite possible. Ubuntu is a fine system.

However, if those who aspire to that goal and wish to push Ubuntu ahead, you will need to realize what the GUI means to success. Keeping your difficult to learn, memory intensive, blurred finger actions to your self and those in your IT department, is one of the keys to Ubuntu's success. if you continue to point out everyones shortcomings because they have not endeavored to follow your path, you retard Ubuntu more than you realize. If you care, you will have to refrain from your boastful comments about the CLI.  

Ubuntu is locked in place for slow growth with a very determined limiting factor because of those who advocate the Command Line and spending time learning. Do you sincerely think that new people *want* to spend years learning things they prefer to do without, don't need, and don't want? The obvious answer is no. New people want the GUI.

So what's the beef?  Do you think those programmers who show such limitless skill cannot accomplish both?  Of course they can! Those guys, bless them, are fountains of extreme skill. They too however must recognize the GUI. It is a necessary prelude to furthering Ubuntu's success.  

Were I to make an advisement to Ubuntu as I have many major companies I have helped become much larger, finally attain their difficult goals, and produce something to be extremely proud of, I would say this: diminish the CLI in as many ways as you can, but leave it in for those who wish it--for a while.  Then move your people to recognize the necessity of bringing Ubuntu to a 100% GUI with beautiful, no, make that stunning graphics, and a perfectly done documentation suitable for beginners. Keeping the CLI a secret. Do i hear applause? Probably not, and such is the problem. 

If you doubt me, consider that I have placed 14 completely unknown companies into the fortune 500 list. They got there because they stopped agonizing over what they wanted, and began to work on what they needed--what the public (thier customers) needed. 

To advance rapidly, Ubuntu needs a sweet, easily mousable GUI that incorporates beautiful graphics, an easily followed menu, and documentation that everyone can understand and follow. Frankly, as it is now, they are doomed to a very slow rise from the position they hold, which is somewhat like a Good-Old-Boys club--one that sneers at newcomers who don't know the strange and confusing command line that is so poorly documented. Sneers and ridicules those who will take Ubuntu to the top. Now is that a good plan?

Ubuntu, if you wish to grow, contact me. I can guarantees success you may have not thought possible.

---

### Post by bk60544 on 2011-03-27
>>COJON is absolutely on target.  Look at the Mac vs. PC evolution.  Mac grew because of GUI, and then stalled/slid back as it became more "DOS-like" and Windows improved its GUI.  I am new to Linux and impressed with Ubuntu and am **struggling** more than I expected.  
>>The other obstacle to Linux acceptance is TERMINOLOGY.  Learning a new OS can be challenging enough; having to learn a new *language* is driving potential users away in droves.  And is anyone thinking about the importance of the terms selected?  "Grubs" are why I buy insecticide!!  "Kernels" are the annoying parts of popcorn that gets stuck between your teeth.  _Words do matte_r.  GM learned that the hard way when it found that sellingl the Chevy *Nova* to spanish-speaking consumers was a NO-GO.
>>"Millions of drills are sold each year.  Not because people want drills, they want HOLES."  People are looking at Linux/Ubuntu because they want a less expensive, less vulnerable and** EASIER **OS, **not** because they want to **LEARN** a new OS.
>>Microsoft grew not so much because they had a good product, but because they had good marketing.  And good marketing people know that "perception is everything".  Linux developers and advocates need to think about the average user rather impressing colleagues or geeks when choosing words, descriptions, and titles.

---

### Post by Chriske on 2011-04-30
Thank you Unknown Hero. Your post was very helpful to me.

\\:D/

---

