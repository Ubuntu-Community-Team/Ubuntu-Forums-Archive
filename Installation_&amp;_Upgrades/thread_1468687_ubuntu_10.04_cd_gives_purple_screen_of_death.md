---
title: "ubuntu 10.04 cd gives purple screen of death"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by groovomata on 2010-05-01
Hello All, I've installed almost every version of ubuntu so far and four different versions on this computer, and I've never had a problem with the installation cd. The install cd on this new version however gives me only a purple screen of death with a white line down the middle. What is going on? The ubuntu-10.04-desktop-i386.iso file's md5sum is fine. I've burned it successfully on two different discs and still I can't install it. 

I've got a Dell 6400 with an nvidia geForce 7300 video card. 

If anyone has any ideas I'd love to hear them,
Thank you,
Erik Henriksen.

---

### Post by groovomata on 2010-05-02
Okay, a screen will appear with icons of a little keyboard and a person or something, if I press a key right away I come up with the ubuntu main menu where you can try ubuntu without installing it, you can install ubuntu or you can do a memory test... etc. After that point, no matter what I choose, I alway end up with something that looks like a purple kind of background with a white stripe going down the middle:
[IMG]http://www.flickr.com/photos/86733040@N00/4570180734/sizes/o/[/IMG]

---

### Post by lawalty on 2010-05-02
Same here.  I installed ubuntu 9.10 32bit and 64bit without any issues.  I even installed ubuntu 10.04 32bit very smoothly, but trying to install ubuntu 10.04 64bit gives me the same issue of seeing a bunch of white vertical lines in some type of pattern.  It's like it's not showing whats is happening behind the lines.

[CENTER]:confused:  
[/CENTER]

---

### Post by itilious on 2010-05-02
> **lawalty said:**
> Same here.  I installed ubuntu 9.10 32bit and 64bit without any issues.  I even installed ubuntu 10.04 32bit very smoothly, but trying to install ubuntu 10.04 64bit gives me the same issue of seeing a bunch of white vertical lines in some type of pattern.  It's like it's not showing whats is happening behind the lines.

[CENTER]:confused:  
[/CENTER]


SAME HERE and its driving me INSANE, I think it ruined my installation because i can't even boot, all i can do for the meantime is use the 10.04 LIVE CD :( :(

---

### Post by groovomata on 2010-05-02
For me the issue is that I can't even use the live cd, as that's what I see and I haven't even installed 10.04 yet. I'm using Linux Mint right now, and I was thinking of installing ubuntu 9.10 and then doing an upgrade but now I'm not so sure.

---

### Post by Rahu on 2010-05-02
I'm getting the same thing, from what I can tell its an issue with the nouveau driver.

When I did the server install it managed to put up an error before the purple.


nouveau: pointer to LVDS manufacturer table invalid

---

### Post by pommest on 2010-05-03
I also try to install Ubuntu 10.4 LTS 32bit on my notebook. 
I have an Intel P8600 2.4ghz and a Nvidia 9600m gt... 

When i press Install Ubuntu, the ubuntu screen freezes...
After I press the escape-key i can see the following Errorline:

prozess:404: Glib-Warning **: getpwuid_r(): failed due to unknown user id (0)

Before I formatted my Harddisk i had installed ubuntu 9.10 and it ran perfectly!

I know my English is bad, but please help me to get the new Ubuntu 10.4.

greets
pommest

---

### Post by 1awesomeguy on 2010-05-03
I am having the same issue here. Yesterday, I tried upgrading through the upgrade utility from Ubuntu 9.10. There was an error, but the upgrade finished. I restarted and now Ubuntu does not boot. All that happens is I get some kind of fsck ("fsck from util-linux ng" or similar) message and then a black screen.

When I boot from the 10.04 live cd, I get stuck on the purple screen with the little guy and the keyboard at the bottom. If I press enter right away as the OP suggested, I get sent to the install main menu. Any select I make freezes the install and then I get stuck again.

I also tried running the alternative (text-based) install, but then I do not get any error message and just get stuck on a black screen.

I have also tried running a 9.10 live cd, but now that just shows a black screen as well.

---

### Post by techunit on 2010-05-03
You need to enable safe graphics mode or something.. Give me second to look it up. I think you hit F4 or something of that nature but I will check.

Edit:

Ok when you start the Live CD hit "Esc" so you bring up the menu. then hit "F4" and choose safe graphics mode...

Good Luck...

---

### Post by 1awesomeguy on 2010-05-03
> **techunit said:**
> You need to enable safe graphics mode or something.. Give me second to look it up. I think you hit F6 or something of that nature but I will check.

Thanks techunit. I have an older Intel graphics card (integrated into the motherboard of the laptop) on this five-year-old computer.

I have never had a problem on this laptop with any previous version of Ubuntu. Seems like they may have rushed this release to get it out in time...

EDIT: All I get in the F4 'Modes' menu is: 'Normal', 'Use driver update disc', and 'OEM install (for manufacturers)'

---

### Post by techunit on 2010-05-03
> **pommest said:**
> I also try to install Ubuntu 10.4 LTS 32bit on my notebook. 
I have an Intel P8600 2.4ghz and a Nvidia 9600m gt... 

When i press Install Ubuntu, the ubuntu screen freezes...
After I press the escape-key i can see the following Errorline:

prozess:404: Glib-Warning **: getpwuid_r(): failed due to unknown user id (0)

Before I formatted my Harddisk i had installed ubuntu 9.10 and it ran perfectly!

I know my English is bad, but please help me to get the new Ubuntu 10.4.

greets
pommest

Make sure that the CD was burned correctly, If it wasn't then you will have problems. I found this to be a problem but using imgburn in windows did the trick.

---

### Post by 1awesomeguy on 2010-05-03
> **techunit said:**
> Make sure that the CD was burned correctly, If it wasn't then you will have problems. I found this to be a problem but using imgburn in windows did the trick.

I used Brasero on all the disks, but for me personally (not sure about pommest), I find it unlikely that all four of the disks had errors. The 9.10 disk was used previously without any errors to install Ubuntu on two other computers (as well as this computer last year).

I will download a new ISO from ubuntu.com, install K3b, and test with a fresh cd. Will report back.

---

### Post by 1awesomeguy on 2010-05-03
I downloaded a new live cd .iso from ubuntu.com. I burned it with K3b and checked for errors. I booted the broken laptop with the dvd inside and didn't press anything (expect my bios password). The Ubuntu logo came up this time with the loading circles. After that, I just get a black screen.

EDIT: Same thing happens if I go to the menu and try to "Install Ubuntu" directly.

EDIT 2: Ubuntu's official error-check on the live cd says "Checking finished: no errors found"

---

### Post by lawalty on 2010-05-03
SOLVED!!  Okay! i found a solution (workaround) to this issue!  It DOES have to do with the graphics card.  You just have to install the operating system using the low graphics mode.  Make sure when you follow these steps, your machine is connected (hardwired) to the internet.

1st.  Put your burned ISO 64-bit disk into the CD/DVD drive.

2nd. Start your computer.

3rd. When you see the Keyboard and Little man - press the space bar.

4th. Select your language.

5th. Use the arrow keys and highlight 'Install Ubuntu' - don't click enter yet.

6th. Press F6 - Use the arrow keys and highlight 'nomodeset' then press spacebar.

7th. Press the 'ESC' key - to get back to the original menu.

8th. Since you highlighted the 'Install Ubuntu' option, then click Enter.

9th. Go through the Ubuntu install

After install, you will need to boot up into your new Ubuntu OS forcing it in Low Graphics mode.

1st. When booting (hold down the shift key) - this brings up Grub.

2nd. Use the arrow keys to highlight the recovery mode - then click enter.

3rd. When the next menu appears - use arrow keys to select 'failsafeX' - this will force Ubuntu to run is low-graphics mode.

4th. Select 'OK' on the confirmation prompt.

5th. It will then ask you what you like to do - Select the 'Run Ubuntu in low-graphics mose for this one session'.

6th. When you are (finally) at your desktop - make sure you are connected to the internet, and install your (MUCH NEEDED) graphics card drivers.

then - reboot.

This is the step-by-step method on my workaround to get my 64bit (totally AWESOME) Ubuntu 10.04 installed on my Compac Presario F700 AMD64 Athlon x2 (4gigs RAM) 120gig HD.

[CENTER]:KS
[/CENTER]

---

### Post by 1awesomeguy on 2010-05-04
lawalty's exact solution did not work for me. I found a solution on another thread which appears to have fixed my problem and got the live cd running: [http://ubuntuforums.org/showthread.php?p=9207606#post9207606](http://ubuntuforums.org/showthread.php?p=9207606#post9207606)

EDIT: I have an Intel graphics card a 32 bit processor.

---

### Post by Rahu on 2010-05-04
Lawalty's solution worked for me to the point of getting it installed, but nouveau is still crashing in the same manner when I attempt to start up in recovery mode after the install.

Is there some way I can boot straight to a CLI to fix this without attempting to load X?

---

### Post by robert shearer on 2010-05-04
Just a possible addition to lawalty's fix,

I had to also select, at the F6 menu, "nodmraid" otherwise the install started without x and scrolled to a stop with a reported 'soft cpu lockup' and repeated that line over and over.

---

### Post by groovomata on 2010-05-04
I found another thread on what looks like the same issue, which also has an apparent solution. I'll give it a try and see it if works.
[http://ubuntuforums.org/showthread.php?t=1465768&page=4](http://ubuntuforums.org/showthread.php?t=1465768&page=4)

---

### Post by groovomata on 2010-05-05
Check out this post, it may be of interest:

[http://ubuntuforums.org/showthread.p...95#post9239795](http://ubuntuforums.org/showthread.p...95#post9239795)

---

### Post by AsianSpanker on 2010-05-31
> **groovomata said:**
> Hello All, I've installed almost every version of ubuntu so far and four different versions on this computer, and I've never had a problem with the installation cd. The install cd on this new version however gives me only a purple screen of death with a white line down the middle. What is going on? The ubuntu-10.04-desktop-i386.iso file's md5sum is fine. I've burned it successfully on two different discs and still I can't install it. 

I've got a Dell 6400 with an nvidia geForce 7300 video card. 

If anyone has any ideas I'd love to hear them,
Thank you,
Erik Henriksen.

I have a Dell Dimension 9100 and upgraded from 9.10 to 10.04 and now also have the purple screen of death. No letters or numbers of any kind. A bit of Klingon (just white marks that can't be letters, on the bottom of screen) Am turning it off and by pushing down on the Main Box start key, but all I get is the purple screen of death. Any remedies???? I am using my laptop to write this.

---

### Post by MimeyNaomi on 2010-06-02
Hi, I was having a problem where the install would at least START, let me get through all my keyboard settings and username and formatting preferences, and then crash at about 24% of copying files.  I'd get "Glib-Warning **: getpwuid_r(): failed due to unknown user id (0)" and a few other lines for just a few seconds, and then flashing white vertical lines on a black background, and that was the end of everything.

This seems to have fixed it so far (crossing my fingers, got to 79% [scanning cd-rom] at this point):

hit space at the keyboard/dude, hit F6, select acpi=off, noapic, and nomodeset, then install.

Will update if doesn't work.  If no update, it worked.

---

### Post by MimeyNaomi on 2010-06-02
Installation completed successfully.  Now, when trying to boot, I start to get the Ubuntu splash screen, then random red pixels, then the blinking white lines.  Time for me to find another thread, I think.

---

### Post by priyank566 on 2010-06-14
> **groovomata said:**
> For me the issue is that I can't even use the live cd, as that's what I see and I haven't even installed 10.04 yet. I'm using Linux Mint right now, and I was thinking of installing ubuntu 9.10 and then doing an upgrade but now I'm not so sure.
hey plz dont try that
dont upgrade from 9.10 to 10.4
bcoz i hv tried it already and didnt work 
same blank screen appears and no ubuntu is loaded
so try installing kubuntu 10.4
may b it'll work

---

