---
title: "linuxant -winmodem"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by pugrit on 2005-03-16
has someone successfuly installed this driver for winmodems?first hand expereince will surely help a lot.

tried installing it with the .deb but it says package not found even though im sure i got it correctly spelled.

tried also the .tar and insatlled it but the problem is when i type in hsfconfig

it would ask:

where is the linux source build directory that mathes your running kernel? [/usr/src/linux]

i typed in usr

but still the driver wont insatll..theirs still an error and the instalation wont continue.

any suggestions?

thanks

---

### Post by m4ng0 on 2005-03-16
If you want to use the .deb, type:
sudo dpkg -i pathtoyourfile.deb

If you want to use the tar.gz, you have to compile, so you need:
build-essential
and
linux-headers

---

### Post by pugrit on 2005-03-17
thanks.

are they all in the package manager?
anyways, il try it.

thanks.

---

### Post by Michele Moglia on 2005-03-17
I did not have any problem with the linuxant drivers.
I think they want the linux source dir (/usr/src/linux)
to discover the kernel version so if you install
the packages as the the prevoius post told you
you will manage to configure the drivers.

michele

---

### Post by pugrit on 2005-03-18
intsalled already the build-essential and linux headers.

typed in hsfconfig

and still problem. this time:

1.>

pre-built modules for debian-testing/unstable linux-2.6.8.1-3-386 i686

where is the linux build directory that matches your running kernel?

[lib/modules/2.6.8.1-3-386..] 

typed in usr

warning the kernel version (2.60-test7) defined in the /usr/include/linux/version.h) does not match the currently running kernel (2.6.8.1-3-386)

the casue of this problem is an incorrect kernel source path. please check that the /user points to the right tree.

however, proper /boot/config-2.6.8.1-3-386 was found

would you like to try using it.

typed in yes

after a few minutes..

unable to prepare temporary kernel tree

*********
2.

i also tried the sudo dpkg but it still takes me to 1.

****

3. 

any other solutions? do i have to re-insatll ubuntu? im sure the modem works casue linuxant detects it. but th eproblem is insatling the driver since my ubuntu instalations seems not to know where the proper directories are.

any help will surely help a lot.

thank you very much.

---

### Post by pugrit on 2005-03-19
any other help from this?

---

### Post by gremeth on 2005-03-21
> warning the kernel version (2.60-test7) defined in the /usr/include/linux/version.h) does not match the currently running kernel (2.6.8.1-3-386)
Are your kernel sources congruent with the kernel you're actually running?

---

### Post by pugrit on 2005-03-22
i just followed the insatlation procedures. dualboot with xp. partioned hardisk. everything wokrs great except of course for my winmodem.

i dont know whats wrong with it. i cant trace it.

iv insatlled th ebuild essentials and headers but still somethings wrong.
.

the first problem was autoconfig.h not found.
solved this on eby insatlling th ebuild essentials and headers.

tried running hsfconfig again and this time its the version.h

any suggestions?my last resort would be re-insatll. but i doubt it will wokr but still, im open to ideas just to get this working.

---

### Post by Enfors on 2005-03-22
[QUOTE=pugrit]
it would ask:

where is the linux source build directory that mathes your running kernel? [/usr/src/linux]

i typed in usr
[/QUOTE]

It seems to me like you're misunderstanding this question. When it says "/usr/src/linux" it doesn't mean "choose between usr, src and linux". It's not a multiple choice question. "/usr/src/linux" is ONE possible answer, not three. The reason why it's printed is because it's the default answer - in other words, if you just hit enter at that question without typing anything. the system will act as if you typed "/usr/src/linux". Try doing that (just hitting enter) and see if that works.

I'm not sure how familiar you are with filesystems, but in linux, "/usr/src/linux" basically means what "c:\usr\src\linux" would mean in the Windows world.

---

### Post by azeem on 2005-03-22
Hi all! (this is my first post in this forum :-))

I'm facing a similar problem, I'm installing the driver for my 56k modem and the installation help text file asks me where is the 'kernel directory' of my operative system.

(there is a variable called KERNEL_DIR which is supposed to be filled with 'path/to/linux')

In my case the default directory is '/lib/modules/$(shell uname -r)/build>'
the (only) other suggestion is '/usr/src/linux-<version>'

Searching through my directories I can't find any directory that seems to the two mentioned above.. (and I'm looking at the directories in Mandrake 10.1, since I have another pc with this distribution, too.)

Anyone can tell me which is the correct 'kernel directory' that the program is asking me?

thanks in advance.

---

### Post by az on 2005-03-22
[QUOTE=azeem]Hi all! (this is my first post in this forum :-))

I'm facing a similar problem, I'm installing the driver for my 56k modem and the installation help text file asks me where is the 'kernel directory' of my operative system.

(there is a variable called KERNEL_DIR which is supposed to be filled with 'path/to/linux')

In my case the default directory is '/lib/modules/$(shell uname -r)/build>'
the (only) other suggestion is '/usr/src/linux-<version>'

Searching through my directories I can't find any directory that seems to the two mentioned above.. (and I'm looking at the directories in Mandrake 10.1, since I have another pc with this distribution, too.)

Anyone can tell me which is the correct 'kernel directory' that the program is asking me?

thanks in advance.[/QUOTE]


install build-essential and linux-headers-(version which matches your kernel (type uname -r in a terminal))
That will make a directory called  /usr/src/linux-headers-2.6.8.1.....
This directory will also be symlinked to /lib/modules/2.6.8.1.../build

It should work out-of-the box most of the time.  If not, tell it to use /usr/src/linux-headers-2.(whatever version) by hand, when prompted.

The people at linuxant should offer better support for their product, since they sell it.  

If you do not care about using free software (by using a comercial, proprietairy, closed-source driver), you should at least demand better service for what you pay.

---

### Post by azeem on 2005-03-22
thank you azz very much for your help, I'll tell you if all will work fine (I'm on another computer now..)

[QUOTE=azz] The people at linuxant should offer better support for their product, since they sell it.[/QUOTE]
I have to say that the support I mentioned didn't come from linuxant, my 56k modem is from another company (I don't remember the name). It came integrated with my mother's laptop.

[QUOTE=azz] If you do not care about using free software (by using a comercial, proprietairy, closed-source driver), you should at least demand better service for what you pay.[/QUOTE]
I do not understand you very much here: I do care about using free software (this is one reason why I'm trying ubuntu), but how can I avoid using a comercial, proprietairy, closed-source driver?
(warning: my questions could be silly, due to the fact I'm newbie..)

---

### Post by az on 2005-03-22
"but how can I avoid using a comercial, proprietairy, closed-source driver?
(warning: my questions could be silly, due to the fact I'm newbie..)"

This is not at all a silly question.

Linuxant provides a driver for 14.99 US dollars.  It is closed source and proprietary.  You can wither encourage them (and conexant) and buy their driver (which is only supported for a year, or so.  After than, if you want to update your kernel, you will have to pay them again for a new driver that will work with the next kernel)  Their product only runs on an open source operating system, but it is not open source, nor free (as in liberty).


You have a choice.  You can spend the same amount of money (often, less) and buy a modem with a chipset from a company that cares more about your freedom to use open source software.  Intel and Lucent come to mind.  These things change often, as these companies change ownership sometimes.

You can also buy a hardware modem.  But that is often more expensive.

---

