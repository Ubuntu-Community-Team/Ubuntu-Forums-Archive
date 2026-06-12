---
title: "Confusion with Installation Instructions"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by lusbyclark on 2013-03-24
I am trying to create a CD that will allow me to install Ubuntu 12.04 onto a PC.  \

The first instruction is to put a new DVD into the drive and then wait for a window to pop up that we are told to close because we will not be using it.  

The next instruction is the look for the ISO file with (or in) the File Browser.    What is a File Browser?  And will there be more than a single file with this ISO name?

---

### Post by oldos2er on 2013-03-24
What OS are you using?

---

### Post by lusbyclark on 2013-03-24
Currently I am using Ubuntu 12.04 32-bit.  I want to upgrade to the 64-bit Ubuntu.

---

### Post by ManamiVixen on 2013-03-24
Its located in the downloads folder in Home if you used the direct download. If you want 64bit, please tell us what Computer you have? It might not support 64Bit, but it could if you tell us.

---

### Post by lusbyclark on 2013-03-24
It is a generic PC with a GIGABYTE mother board (either a GA--Z77-DS3H or GA-H77-DS3H) with in Intel Core i5-3330 CPU @3.00GHzX4.  It is the same mother board with a very similar CPU I have in another generic PC that is, indeed, running the 64 bit version of Ubuntu.  It has 8 GBYTES of RAM and a 240 GBYTE SSD.  If you need more info, let me know.  I am more than glad to help.

---

### Post by oldos2er on 2013-03-24
> **lusbyclark said:**
> Currently I am using Ubuntu 12.04 32-bit.  I want to upgrade to the 64-bit Ubuntu.

If you're using Unity, Nautilus is your file browser.

---

### Post by lusbyclark on 2013-03-24
I opened the Dash and searched for Nautilus and found the Home folder and the Files folder were identified as containing something related to this Nautilus thing.  Not surprisingly both the Home and the Files folders contained identical files. I looked in all of the files in both the Home and the Files folders.  Nothing!  Any suggestions about what I am doing wrong?  Also what am I to do with the file browser once I have it in hand?  I know I am to look for some ISO file.  I have already searched for an ISO file and found probably several hundred files with a nmae that included the three letters ISO.  It occurs to me that maybe I have been using the file browser all along and doing so completely unaware it actually has a name. 

Please bare with me for the moment.  What I really want to do is to downbload the Ubuntu 12.04 64-bit stuff to a CD/DVD that will allow me to install it to this PC. It should also include the usual load of monitor drivers as well as the drivers for other such peripheral devices.

---

### Post by oldos2er on 2013-03-25
The ISO file you want is named ubuntu-12.04.2-desktop-amd64.iso

In Linux, drivers for most common hardware are compiled into the kernel. At boot it will detect your hardware and automatically load the drivers it needs. If you have old or very new hardware, drivers may not be available.

There are instructions here on downloading and burning the Ubuntu ISO: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by lusbyclark on 2013-03-25
I am still confused by the instructions.  I know this makes me appear to not only helpless but also hopeless.  I know now I should have posted this thread in the Absolute Beginners section, for an absolute beginner I surely am.   But here I am in the Hardware and Installation section.

The first instruction say load a new CD/DVD in to a burner.  It goes on to say that an instruction window will comes up, and that it should be cancelled or closed because it will not be used.  The next instruction says to look for the downloaded ISO file in the/my/a file browser.  Right click on this ISO file.  

The confusion lies in the past tense word downloaded.  Is it some file that my PC already has stored away somewhere, or is it on a server somewhere?  I am also still confused about the file browser.  I am aware of only two features on this PC that can be used for file browsing/searching: the Dash Home and the Home Folder.  If this ISO file is located on a server somewhere, how do I get to it?  I must say I doubt it is already on my PC, because it is currently running the 32-bit version of Ubuntu 12.04.  The guys at the PC shop where I purchased this PC claimed they were confused about which version of Ubuntu, the 32-bit or 64-bitversion, they should deploy, and the fact that the 64-bit version comes with a prefix of "amd" told them that the 64-bit version only works with AMD processors.

---

### Post by Cheesemill on 2013-03-25
You need to download the iso file yourself before you can burn it to a disk.

The download can be found here...
[http://releases.ubuntu.com/precise/ubuntu-12.04.2-desktop-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.2-desktop-amd64.iso)

---

### Post by lusbyclark on 2013-03-25
[SIZE=2]OK.  As I understand my situation I am to download a file named** ubuntu-12.04.2-desktop**[/SIZE][SIZE=5][SIZE=2]**-amd64.iso** f[/SIZE][SIZE=5][SIZE=2]rom a server (?) at 
**                                  [http://release.ubuntu.com/precise/u...ktop-amd64.is](http://release.ubuntu.com/precise/u...ktop-amd64.is)**[/SIZE][SIZE=5][SIZE=2][B]o.

[/B]Next question: will downloading this .iso file install the 64-bit version of ubuntu 12.04 on my PC?  Or will downloading this .iso file just result in it being stored somewhere on my PC's hard drive?  Will it be in compressed form?  Will I need some way to uncompress the file?  To my knowledge I do not have a decompression application on this PC.  Don't even know the name of such a Linux application.  In any case, once I have this .iso file on my hard drive, I can burn it to a CD/DVD.   [/SIZE]

[/SIZE]
[/SIZE][/SIZE]

---

### Post by Cheesemill on 2013-03-25
Once you have downloaded the iso file to your hard disk you can then burn it to a DVD. The only software you need is a DVD burning application which you already have installed, the iso file is already in the correct format needed to burn it to a disc.

[http://www.ubuntu.com/download/help/burn-a-dvd-on-ubuntu](http://www.ubuntu.com/download/help/burn-a-dvd-on-ubuntu)

---

### Post by Sef on 2013-03-25
> [COLOR=#000000] The next instruction says to look for the downloaded ISO file in the/my/a file browser. Right click on this ISO file. [/COLOR]

[COLOR=#000000]The confusion lies in the past tense word [/COLOR]*downloaded. Is it some file that my PC already has stored away somewhere, or is it on a server somewhere?*

Downloaded in this sense is not a past tense verb, but a past participle functioning as an adjective that is modifying the word file.

---

### Post by oldos2er on 2013-03-25
Please use the default font in accordance with the [posting guidelines]("http://ubuntuforums.org/misc.php?do=showrules").

You don't need to do anything with the ISO other than burn it as an image to a CD or DVD. Once you're done that, reboot with the disc in your computer to begin installation.

---

### Post by lusbyclark on 2013-03-26
I am sorry if my using a font size larger than the default size offended anyone or violated a forum rule.  I did so not as an attempt to gain more attention or to make an emphatic statment by increasing the font size of my messages.  Truly it is because my eyes are not as nearly good as they were fifty years ago and increasing the font size allows me to better see and discern the individual characters as I type and to more easily make typing corrections *in situ*.  Try as I might, I have had no real success over the last fifteen or so years finding a good distance to place a PC monitor in front of my bifocal lenses.   The characters of this default font size are either out of focus fussy or too small to be readable.  To read the characters of this font size, I must stop typing, lean forward and tilt my head backwards placing the document within the field of view of the lower portion of my bifocals.

I can not speak to the mechanisms in this particular writer, but I found that the memory storage requirements for three separate copies of the same LibreOfficeWriter document actually decreased with increasing font size. 

Additionally, many older folks, like myself, have adopted the habit of enlarging the font size in ordinary e-mail communications merely out of courtesy to the intended recipients.  

Finally, I must ask if the default font size is the only acceptable font size for communicating in this forum, why is a font size adjustment provided with this new writer?

---

### Post by oldfred on 2013-03-26
My eye doctor has me on bi-focals just for computer use (about 18" )  & reading. I cannot look at distances with them. It is like trifocals but my vision is bad enough I need the larger area and tri-focals would not work.

You can in Firefox use control + (and -) on just about any screen and make it larger. I use that a lot, but with my new glasses I do not as much as I used to. I prefer to have more info on the screen in many cases. 

If you change the font you force everyone to have less on the screen. 

I used to use CD/DVDs for installs, but when thru a lot of coasters (bad burns) and then with upgrades needed new version. I really liked Linux as when I double click on an ISO it is smart enough to know I want to extract an ISO not copy it to CD or DVD. New versions are now too large for CDs.

Now with flash drives a lot cheaper, I use (and reuse) them. 

Most of what you needed was posted above, some of my standard links which may be duplicates. 
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by oldos2er on 2013-03-26
> **lusbyclark said:**
> Finally, I must ask if the default font size is the only acceptable font size for communicating in this forum, why is a font size adjustment provided with this new writer?

The answer is in the posting guidelines which I linked to earlier: "[COLOR=#000000]Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser."[/COLOR]

---

