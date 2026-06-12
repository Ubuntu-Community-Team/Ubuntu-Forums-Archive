---
title: "Unusual Install Method, serious technical help needed"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-11-28
Hi, i have posted a couple of threads about not being able to install linux (that means ANY distro on ym new Evesham A240 laptop, actually a Clevo M665JE clone).

Sadly i had very few replies. After some extensive googling i found one guy who had the same problem. I emailed him to ask hiim if he had any luck, and here is his reply.




> 
Hello Rob,

Linux-Install is't the problem. You can do it too. Simple use Windows and any virtual machine with direct hard drive access and install your distribution.

The problem is to boot the default kernel, this will stop running analog LiveCD. Also you must build your own kernel with ( 64bit,SATA support, SMP
etc.) an all things you are need.

I'm not a linux guru and have found this idea in a russian ASPLinux forum
[http://asplinuxclub.org/viewtopic.php?id=1358&p=2](http://asplinuxclub.org/viewtopic.php?id=1358&p=2)

The autor 'goblin' have got linux installed this way over virtual machine.
He say that after compile kernel( i can't understand with or without kernel injected ACPI information ) it was possible to boot it.

The only problem was to support sound subsystem( ALSA driver) and it was solved by a forum user ( ALSA patch ).

The latest problem with multiboot if you got boot Windows an do hibernare from it, some BIOS settings( USB BIOS Legacy Support at the last) will be changed on awake from hibernate. After this is not possible to boot the kernel the same ACPI problem.

Another tipp from forum is to use ACPI=legacy options. But i can't find any information about this kernel boot options for 64bit kernel.Documentation bug? Don't known.

So i will play with BIOS settings and test default kernels from Ubuntu or Etch, but yet no time left ;-) some deadlines.

Please mail my you you got more info about linux and 'our' machine.

Regards,
Hermann





Although i understand the basics here, such as compiling my own kernel, i am unsure of what he means / howto go about creating an install through a virtual machine with direct harddrive access. I have used VMWare multiple times but i dont know if this has direct hd access.

Any, help, advice, explanations, technicle break downs regarding the above email would greatly help me.
I also dont speak russian so if anyone can point me in the direction of a russian-to-english translation site or community member who can help.

Thanks

here are my previous threads regarding the issue
[http://www.ubuntuforums.org/showthread.php?t=296228](http://www.ubuntuforums.org/showthread.php?t=296228)
[http://www.ubuntuforums.org/showthread.php?t=303576](http://www.ubuntuforums.org/showthread.php?t=303576)
[http://www.ubuntuforums.org/showthread.php?t=304785](http://www.ubuntuforums.org/showthread.php?t=304785)

EDIT: i just used babelfish.av.com to translate the link but it didnt do a very good job. it may as well have translated it to chinese for all i can understand.

---

### Post by giannisapatis on 2006-11-28
Hi,

I have almost the same problem i cant install anything apart from debian. 

i have post some threads as well but i didnt find any sollution.

If you want you can try debian this worked fine for me so if you be able to configure it it is the same as ubuntu but much more difficulty to configure it.

If you find any workaround please e mail me .

Regards,
Ioannis

---

### Post by renzokuken on 2006-11-28
which version and architecture of debian did you install?

did it require any special boot options?

---

### Post by ciscosurfer on 2006-11-28
Sounds to me like your hardware isn't properly supported via current or for that matter existant drivers.  Getting Linux to run on hardware like these can sometimes be quite difficult.  I really hate to say it, but maybe you should try to find another computer to run Linux on.  I know that's not much help, but if you really want to get it to work, sometimes the best method is to choose a hardware setup that's conducive to the install you are wanting to use.

---

### Post by renzokuken on 2006-11-28
it is possible to get linux running on this laptop, its just not easy.

i really would like to give it a go as it will be a good learning curb. although ive been using linux for a few years now, i never reallydelved much into the hardware side of it.

---

### Post by Cynical on 2006-11-30
Your error message mentioned DSDT (Differentiated System Description Table), which consists of your ACPI settings. Apparently the version on your laptop is buggy. 

Try this guide. I have to warn you though, if you are new to linux this may be a little over your head. (you'll learn a lot at the very least)

[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

---

### Post by giannisapatis on 2006-11-30
Hi,

Here is the download for the debian [http://www.debian.org/CD/](http://www.debian.org/CD/)
 installed is the newest version right 3.10 now but it suppose to be that the 4.0 version is coming out on december.

If you havent try it give it a go is really good i think and the bestthing about it is that the actual stable version is stabe for real not like ubuntu or opensuse.

I am using it for 2 years now but i thought to give you ubuntu a try but i see its still too early thats why i ll keep my debian system.

---

### Post by renzokuken on 2006-11-30
> **Cynical said:**
> Your error message mentioned DSDT (Differentiated System Description Table), which consists of your ACPI settings. Apparently the version on your laptop is buggy. 

Try this guide. I have to warn you though, if you are new to linux this may be a little over your head. (you'll learn a lot at the very least)

[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)


thanks Cynical, i have read that post before,

im quite happy to give it a go but im not quite sure what is involved. as far as i can make out, that gentoo post refers to problems with DSDT once a distro has been installed, and obviously i cant even install. could i just use that procedure to patch the kernel on the ubuntu CD, effectivley remastering the CD?

---

### Post by Cynical on 2006-12-01
I'm pretty sure you can boot using the acpi=off option and then recompile your kernel with support later.

---

### Post by renzokuken on 2006-12-06
Just to let u know i have solved this issue.

I had to disable Legacy USB support and enable SMU in the BIOS and the install went perfectly.

Edgy is running nicely on this laptop now.

However, wireless doesn't seem to work and i'm having trouble with the nVidia drivers.......but they are both other issues.

---

### Post by ciscosurfer on 2006-12-06
If you have solved your issue, then you should change the title of this thread to read something like: SOLVED: Unusual install...

---

### Post by renzokuken on 2006-12-07
i was trying to but couldnt find out how, i remember seeing it somewhere but i forgot where

---

