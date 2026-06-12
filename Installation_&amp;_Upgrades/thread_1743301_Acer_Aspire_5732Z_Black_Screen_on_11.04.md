---
title: "Acer Aspire 5732Z Black Screen on 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by gambothell on 2011-04-29
Hi All -

Is there a problem with Intel video cards and 11.04?

I have tried upgrading and using a live CD and live USB with the same results on this notebook. After upgrading or booting off live CD/USB, I see a black screen, not lit. I can here the login prompt and when I press [Enter] and type my password I hear the Ubuntu theme which means everything is up, but still have a black screen. If I try to go to a console, I am still working with a black screen. Yikes ... I know my Live CD is ok, because it boots fine on my Lenovo S10-3 netbook.

Upgraded from Ubuntu 10.10 32 bit, live CD is 11.04 32 bit. Hardware: Acer Aspire 5732Z with Intel Mobile 4 series chipset integrated graphics controller (rev 09) and 3Gb ram.

---

### Post by misetusame on 2011-04-29
Very same problem with an Acer 5734z.

The grub menu displays, but after that it's a blank screen with no backlight. I can hear Ubuntu's startup sounds. Booting by selecting recovery mode is the same behaviour.

---

### Post by unknown47 on 2011-04-29
**English:**
If it is already installed:
In the grub you press B to edit the kernel line. Add at the end of the line acpi_osi = Linux kernel. Press the brightness up key while starting.
 When you start editing the /etc/rc.local and add before exit 0:
 setpci -s 00:02.0 F4.B=00
 Edit /etc/default/grub, edit the line GRUB_CMDLINE_LINUX_DEFAULT:
 GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash acpi_osi = Linux"
Update grub with:
sudo update-grub2

If not installed:
 Boot from the CD, purple screen is displayed press any key to enter startup options. In the boot options choose the language and press F6. Press ESC and write at the end of the line that says Startup Options:
 acpi_osi = Linux
 Press ENTER to start the LiveCD. When loading up press the brightness keys.

Sorry for my English, Google Translate.

**Español:**
Si ya esta instalado:

En el grub presiona la tecla B para editar la linea del kernel. Agregar en el final de la linea del kernel acpi_osi=Linux. Presionar la tecla de subir el brillo mientras que inicia.
Cuando inicie editar el /etc/rc.local y agregar antes del exit 0:
setpci -s 00:02.0 F4.B=00
Editar el /etc/default/grub, editar la linea GRUB_CMDLINE_LINUX_DEFAULT:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
Actualizar el grub con:
sudo update-grub2

Si no esta instalado:
Bootear desde el CD, cuando aparece la pantalla violeta presiona alguna tecla para acceder a las opciones de inicio. En las opciones de inicio elegir el idioma y apretar F6. Presionar ESC y escribir al final de la linea que dice Opciones de arranque:
acpi_osi=Linux
Presiona ENTER para iniciar el LiveCD. Cuando esta cargando presiona las teclas de subir el brillo.





[IMG]http://dl.dropbox.com/u/11893371/Otras%20imagenes/acpiosilinux.png[/IMG]

---

### Post by misetusame on 2011-04-30
No fix, but progress.

Others have been reporting similar problems
[http://ubuntuforums.org/showthread.php?t=1728783](http://ubuntuforums.org/showthread.php?t=1728783)

I have been able to get minimal graphics working in recovery mode: add "i915.broken=1" to the boot options.
[http://ubuntuforums.org/showpost.php?p=10679178&postcount=10](http://ubuntuforums.org/showpost.php?p=10679178&postcount=10)

---

### Post by misetusame on 2011-04-30
I confirm that unknown47's post **fixed it for me**.

It's a **backlight** problem. The screen was not completely blank.

To reach a stage to be able to even edit the files mentioned by unkown47:

[LIST]
[*]At the grub loading screen, press "e" to edit the line. Add "i915.broken=1" to the boot options. Ctrl+x to boot.
[*]When you get into Ubuntu GUI, follow unknown 47's instructions for "If it is already installed:".
[/LIST]
:D

---

### Post by gambothell on 2011-04-30
:) Thanks Unknown47. Your fix worked for me. I am writing this reply from the LiveCD 11.04. Thanks again Ubuntu community for the quick and professional support.

---

### Post by dan_hurst on 2011-05-05
Yeah, thanks unknown47 - that worked for my Acer 5736Z too.

---

### Post by dan_hurst on 2011-05-08
I still have a problem...  

When I leave my laptop for a while it powers down the screen.  I used to be able to just use the mouse and it turned the screen back on but not any more.

Anyone know how to fix this?

---

### Post by Ephack on 2011-05-10
Yes! It worked also on my Gateway NV78.
Many thanks for that!

---

### Post by bogdan.deren on 2011-05-16
Worked on Emachines E725.
Thx unknown47.

---

### Post by dwankan on 2011-05-18
Yeah, this worked to install, but from there, I still can't get a  desktop.  I tried all of these suggestions, but no matter what, I'm  still booting to black (or no backlight; honestly, no matter what you call it, it isn't working).  Until they fix this, I don't think I'll be  working with Ubuntu 11.  I don't have time to build it myself, probably  because I don't really know enough about the system to do most of these  suggested steps correctly.  
This is frustrating.  I love the freedom of  Ubuntu, but these monitor problems (I've had to redesign through days of  reading forums and opening command prompts and doing things I had no  understanding of on every single install of Ubuntu to get the  monitors to work properly with the OS) are making me miss Windows (which  has always worked with any monitor I plug it into), and that's saying a  whole lot because I hate Microsoft's monopolistic business practices.  I guess that's the cost of a free operating system.

---

### Post by deezer on 2011-05-26
Worked to fix black screen on boot on an eMachines e525 running Ubuntu 11.04

However, there are still problems with the screen brightness.  If I lower it by pushing the up arrow, I can never get it back to max by pushing the down arrow.

---

### Post by rachel1.0 on 2011-06-20
Thank you unknown47! It fixed for me too... HP dv6 2138ca here, intel core i5 with integrated graphics.

I did loose all brightness control, apparently my buttons don't work anymore, but this is a minor issued compared to NOT BOOTING (lol).

---

### Post by jonathan5 on 2011-07-01
Acer Emachine e-525   Ubuntu 11.4  The same problem, black screen. unknown47 advice fixed screen but killed mousepad. Thnx for screen, but how to fix mousepad now? 

Besides, this is quite a big bug :(  for some popular brands of laptops.

---

### Post by foresthill on 2011-07-01
> **jonathan5 said:**
> Acer Emachine e-525   Ubuntu 11.4  The same problem, black screen. unknown47 advice fixed screen but killed mousepad. Thnx for screen, but how to fix mousepad now? 

Besides, this is quite a big bug :(  for some popular brands of laptops.

Yeah, I find it amazing that such a major bug like this ever made it past beta testing. And even more amazing that over 2 months later, there is still no update that fixes the problem.

But at least 10.10 still works, which is where I'm staying until this mess is sorted out.

---

### Post by j0sh78 on 2011-07-14
hi all
i've same problem after upgrade from 10.10 to 11.04 on aspire 5732z
i tried to modify /etc/rc.local but with no luck... i can use my pc just selecting the previous kernel from the grub menu :-(
with latest kernel i get a black screen

---

### Post by mynk on 2011-08-01
Did you get  a fix to this problem? I am seeing my screen remain blank after locking for a long time.

---

### Post by j0sh78 on 2011-08-01
> **mynk said:**
> Did you get  a fix to this problem? I am seeing my screen remain blank after locking for a long time.

i reinstalled the 11.04 from scratch... now it works well

---

### Post by eddie_shark on 2011-09-11
:popcorn: unknown 47 thAnx.. it worked for me..

---

### Post by ubun2warrior on 2011-09-11
> **gambothell said:**
> Hi All -

Is there a problem with Intel video cards and 11.04?

I have tried upgrading and using a live CD and live USB with the same results on this notebook. After upgrading or booting off live CD/USB, I see a black screen, not lit. I can here the login prompt and when I press [Enter] and type my password I hear the Ubuntu theme which means everything is up, but still have a black screen. If I try to go to a console, I am still working with a black screen. Yikes ... I know my Live CD is ok, because it boots fine on my Lenovo S10-3 netbook.

Upgraded from Ubuntu 10.10 32 bit, live CD is 11.04 32 bit. Hardware: Acer Aspire 5732Z with Intel Mobile 4 series chipset integrated graphics controller (rev 09) and 3Gb ram.

Hi gambothell,

I also have an acer laptop 4736z and i faced a similar problem.
So i searched google and other forums. The problem is not with the video cards, the problem is with the linux kernel version.. 

If you run ubuntu 10.04 and 10.10 i am damn sure that it will work very fine but if you switch to 11.04 then you will get a blank screen as you say..

Its a bug of some kind with the kernel.. so the only work around that i found was to downgrade the linux kernel. 11.04 has a kernel version 2.6.38.x (u may check ur kernel version by running this command in your terminal "uname -r"(...without inverted comas )) which is creating the problem, i even tried fedora 15 which comes with the same new linux kernel and the problem is similar.

So i would suggest that you stick to 10.10 or 10.04 and wait for the problem to be fixed, this is safe

but if you want to experiment, you can go ahead with downgrading your kernel version.. for this the first step would be to run 11.04 with nomodeset =1 so that you will actually be able to see ubuntu running on ur laptop..

the next steps are slightly complicated and personally i feel that things might get troublesome so you stick to 10.04 or 10.10


all the best :)

regards
ubun2warrior

---

### Post by jibon_24 on 2011-09-11
@unknown 47 thanks it's working. But when this problem will be fixed.

---

### Post by docmark777 on 2011-09-12
I also would like to know if there is a way to know when this has been fixed. 

I've been googling "no backlight" every month for a long time now. 

This has been screwed up for 6 months. 

Is there a better site to monitor to see if anyone has bothered to fix this. 

Will we have to wait for another full release, or will the daily version have a fix first?

Anyone with good advice would sure be appreciated. 

Thanks,

---

### Post by blackdot on 2012-01-19
Thank you very much **unknown47**.:):):):):):):):)

---

### Post by Rod Weiler on 2012-01-29
**Question 1**: Is this bug already **fixed**?
**Question 2**: Does *unknown47*'s workaround also work when the Notebook **is waking up after hibernate and suspend to RAM**?

Background information: I have an ACER Notebook TravelMate 5735Z. Ubuntu 10.10 is working fine. Using a Live-CD 11.04 (Natty) or 11.10 (Oneiric), the Notebook is booting into a black screen. For the Live-CD, the mentioned boot parameter *acpi_osi=Linux* works fine, but right now I can't test how the Notebook reacts with an installed Natty or Oneiric.

---

### Post by zappa on 2012-03-06
This does fix the problem, thanks unknown47. 
But might I add: also, first choose the correct keyboard. 
Otherwise the brightness button does not work of course. 
You can do this prior to F6 with F3.

---

### Post by krcabrer on 2012-04-29
The problem arise also with Ubuntu 12.04.

I have to use the recovery mode, do all sudo gedit procedures,
and then it works.

Thank your for your help!

---

### Post by Thorsen V on 2012-05-01
> **krcabrer said:**
> The problem arise also with Ubuntu 12.04.

I have to use the recovery mode, do all sudo gedit procedures,
and then it works.

Thank your for your help!
I find myself with this problem too, but without a solution.
I have an emachines e525 laptop which has the Intel Mobile 4 Series Integrated Graphics Controller which doesn't seem to work with current generation of distros (!?).
For at least a year just about any LiveCD  I've tried (it isn't just Ubuntu) has had the blank screen/backlight problem.
Anyway, today I decided to try Ubuntu 12.04 regardless, installing onto a new HD and using the full disk. I used nomodeset and the recommended acpi_osi=Linux to get a VGA type display.
The install was quick though, and apparently flawless, but when the machine rebooted, there as I feared was the black screen/backlight problem.
At this point I fell rather stuck. When the machine boots, it goes straight into the HD boots so there is no opportunity to specify any boot options, and if I boot of the CD media and manually edit the rc.local and grub as has been suggested, I can't of course successfully run update-grub2 because the machine hasn't booted off that drive!
I feel painted in a corner. 
Can someone help?

Also can someone clarify if I'm going to be stuck with VGA (low resolution and the wrong aspect ratio) even if I can get the boot to include the acpi_osi=Linux thing?

Thanks for any help.

---

### Post by Thorsen V on 2012-05-01
I thought there was nothing to lose so, despite the warnings, I decided to edit /boot/grub/grub.cfg manually (boot from Knoppix CD).

I added nomodeset to the first line beginning:

```
linux    /boot/vmlinuz-

```which I presume is the normal boot line.
At the reboot this time it started with a visible VGA screen.

 So I edited the rc.local and grub files as described previously and ran update-grub2.
At the reboot this time I had full resolution graphics.

Checking the grub.cfg afterwards the edited line now looks like this:

```
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=dcb34693-7c0a-4106-8eeb-66c04fb45b33 ro   quiet splash acpi_osi=Linux $vt_handoff

```Which is interesting because when I tried to manually edit that line with "acpi_osi=Linux" that didn't work (and I had to add the nomodeset).

Also found elsewhere, before being successful I tried "acpi_backlight=vendor" which didn't  do anything for me but may be useful to someone else.

---

### Post by Atomic-Fanboy on 2012-05-20
This is something I don't understand.... Intel Mobile Graphics v4 chipsets are extremely common, so this issue should have been considered a priority - especially when releasing a "Long Term Support" version of Ubuntu.   Alongside other glitches like the unwelcome sudden screen flicker and non-functional brightness settings, this does not give a new user a very good first impression of GNU Linux, and especially not Ubuntu (which was designed with user-friendliness in mind.)

---

### Post by rivalarrival on 2012-06-19
Thank you! I've spent about 6 hours trying to get this to work. Now I can get back to the problem I was trying to fix 8 hours ago that necessitated the 2-hour upgrade from 10.04 to 12.04 that broke this.

---

### Post by Mrricheyrich on 2012-07-01
Hi,
I have precisely the same problem with the non-back lit screen (Acer Aspire 5732Z). I can confirm Unknown74's live boot workaround worked for me, but unfortunately the method for the installed version didn't.

Pressing shift on startup took me to grub, which I edited (pressing "e"). I added the
>acpi_osi=Linux
entry to the bottom of the grub and reloaded (ctl-x). No success.

I also tried the
>i915.broken=1
suggestion from misetusame (apparently for Intel graphic chipsets, which I have). Also no joy.

Instead I used the recovery mode, got the command prompt and tried to change "rc.local" and "grub" in the way described by Unknown74. Problem is, I have no write permission and Linux tells me it can't create a swapfile. I've tried using nano and vi with sudo but I still can't get write privileges.

What on earth am I doing wrong? I am at the very limit of my Linux knowledge so would be very grateful for any Linux-for-dummies responses!
Cheers,
Rich

---

### Post by houndnews on 2012-07-05
Hello Mrricheyrich

Have a 5732Z myself with linuxmint 13 installed using i915 graphics.  If you can get to the install screen (I'm using a 12.04 disk not 11.04) "Try Ubuntu..." "Install Ubuntu" etc (I had to hit the arrow down key just after the first splash screen displays) select F6 "Other Options" then arrow down to "nomodeset", hit Enter to select (an x should appear), then  Esc and Enter again.  You should be able to get a gui and install from there.  Before shutdown edit /etc/default/grub as root and add nomodeset after "quiet splash"  and I added "setpci -s 00:02.0 F4.B=00" just before exit 0 in /etc/rc.local.  I'm assuming Mint is the same as Ubuntu here. Don't forget to update-grub.  

Check out this link if you have a resume from hibernation problem, see screen.brightness script
[http://ubuntuforums.org/showthread.php?t=1744809](http://ubuntuforums.org/showthread.php?t=1744809)

You will be stuck with low end graphics driver, at least I am.  If you find out different post back.

---

### Post by houndnews on 2012-07-14
Acer 5732Z working Mint 13 Cinnamon 64 bit. See details at
[http://forums.linuxmint.com/viewtopic.php?f=49&t=107612](http://forums.linuxmint.com/viewtopic.php?f=49&t=107612)

Working confiuration i915 as graphics driver in /etc/X11/xorg.conf (Driver  "i915" in Section "Device"), "quiet splash acpi_osi=Linux" in /etc/default/grub (need to run "update-grub" if changed), and setpci -s 00:02.0 F4.B=40 in /etc/rc.local just before exit 0 (last two digits control initial brightness 00 is full on FF is off).  Installed latest xserver-xorg-video-intel 2:2.19.0~precise~ by adding new ppa as mentioned here [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver) , but this may not be necessary, 2.17 supplied with the distro may work.

---

### Post by Rod Weiler on 2012-11-30
I found solutions for my Notebook **Acer TravelMate 5735Z** for a) Ubuntu 12.10 (Quantal Queezal) and b) Ubuntu 12.04 LTS (Precise Pangolin). See my [comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438/comments/112") to the bug#765438 on Launchpad ([Link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438/comments/112")).

Maybe it helps someone.

---

### Post by apv1224 on 2013-01-22
Work on 5732Z thx unknown 47!! :D

---

