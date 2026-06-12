---
title: "HP tx1340 (it it going to work)"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by p07gbar on 2008-01-15
I am thinking of buying the HP tx1340 but I want to know if the touch screen will work. It rus Vista.

---

### Post by BUNTUNSE on 2008-01-26
I have tx1340, running vista. The last 24 hours I have been trying to install ubuntu to no avail. I have tried versions 7.10, 7.04, 6.06 as well as the 7.10 Alternate.

My son managed to install on his ecer laptop we bought in 2005.

The nearest success is running in "safe mode", where I have been able to see what ubuntu looks like on the tx1340. I am now going to try to install from inside the "safe mode". I hope it will still be safe, and I hope that some experienced users and moderators can help us.:confused:

---

### Post by BUNTUNSE on 2008-01-27
:(Further to my post yesterday on HP Pavilion TX1340 and Ubuntu, I can now sadly report that Ubuntu failed to install on the TX1340 laptop. It went as far as 15% on partitioning the HDD, and hang up there.

I had to reboot the laptop, however by this time the windows vista partition became corrupted and boot failed. SO? I had to reinstall windows vista since I have installation DVD, and later I had to restore the machine to factory shipped state (having earlier on made copies of image).

We still need help from the moderators or experienced members.

---

### Post by Lupus Umbrae on 2008-03-03
I've just recently got a TX1340ea and have managed to get Ubuntu installed.

The first issue i had was running the live CD i had graphics issues but manged to fix them by
1) pressing f6
2) moving left and hitting f1 twice (You get a command screen)
3) Typing "live vga=771 noapic colapic"

Once in i installed ubuntu but preserved the recovery partition (use manual parition delete the large one leave the small one).

After getting it installed i've been fighting to get wireless, sound and touchscreen.

Got touchscreen working it just doesnt stay working

---

### Post by rebshalom on 2008-03-03
I have the tx1320us. I managed to install Ubuntu but had and still have problems.
Instead of partioning the hard drive and leaving the Vista partion, it took the whole drive.
I cannot access any ports on the computer either USB or ethernet.
Of course wireless is out of the question.
Hope this helps

---

### Post by confuded92 on 2008-03-09
Hello,

I own a HP Pavilion tx1340ea and have installed ubuntu on it dual booting crap.. I mean Vista.

Everything works besides the following:
audio - no luck, wifi - can be done through ndiswraper and touchscreen - which I really like to get working. I am not complaining about the webcam, since i know thats never going to work :(. 

Has anyone got any advice on the audio problem? Thanks.

---

### Post by Lupus Umbrae on 2008-04-06
I've gotten the touchscreen and the audio to work.

The touchscreen is pretty easy when you know how.
1) get the drivers from [http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

2) Extract the drivers to "var/lib"

3) Add the following to your xorg.conf
```

Section "InputDevice"
	Identifier	"EETI"
	Driver	"egalax"
	Option	"DeviceName"	"EETI"
	Option	"Device"	"/dev/usb/hiddev0"
	Option	"Parameters"	"/var/lib/egalax.cal"
	Option	"ScreenNo"	"0"
EndSection

```
Under server layout add
```
InputDevice	"EETI" "SendCoreEvents"
```

4) Lastly open up etc/modprobe.d/blacklist

```

#Cause touchscreen drivers to malfunction
blacklist usbtouchscreen
blacklist tkusb

```

5) once you restart you'll need to run the touchkit to calibrate the touchscreen (mine was upside down!!). You'll need to run as an admin so terminal sudo ..../touchkit depends where you put it.

This worked for me. hope it works for you too

---

### Post by BUNTUNSE on 2008-04-12
> **Lupus Umbrae said:**
> I've gotten the touchscreen and the audio to work.

The touchscreen is pretty easy when you know how.
1) get the drivers from [http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

2) Extract the drivers to "var/lib"

3) Add the following to your xorg.conf
```

Section "InputDevice"
	Identifier	"EETI"
	Driver	"egalax"
	Option	"DeviceName"	"EETI"
	Option	"Device"	"/dev/usb/hiddev0"
	Option	"Parameters"	"/var/lib/egalax.cal"
	Option	"ScreenNo"	"0"
EndSection

```
Under server layout add
```
InputDevice	"EETI" "SendCoreEvents"
```

4) Lastly open up etc/modprobe.d/blacklist

```

#Cause touchscreen drivers to malfunction
blacklist usbtouchscreen
blacklist tkusb

```

5) once you restart you'll need to run the touchkit to calibrate the touchscreen (mine was upside down!!). You'll need to run as an admin so terminal sudo ..../touchkit depends where you put it.

This worked for me. hope it works for you too

I also own a tx1340ea. I have been trying to get the touchscreen work by following your guidance here. Sadly when I sudo '/var/lib/touchkit', I get the warning to make sure '...X...' is installed. When I click to proceed, I get no where with the process as the warning only disappears.

Do you have anymore advice? By the way, I have installed the Ubuntu 8.04 Alpha 6.:confused:

---

### Post by twist2b on 2008-04-12
Yes I have the tx1000 series aswell. Heres how you install.

YOU CANT GET GUSTY! (7.10) you can but you dont seem computer savvy, if you want it I will tell you how (just pm me)
get 7.04 and install
it will black screen on boot so go into recovery mode and type this:
apt-get update
apt-get install nvidia-glx-new
then after installing the correct drivers
dpkg-reconfigure xserver-xorg
now change from vesa driver to the newly added "nvidia" (or if you got gusty switch from nv to nvidia)
finnish up the steps and it works.
Hardy Heron Beta works from start. I suggest getting that if your lazy :P
just because its beta does not mean its bad. Its way better then Gusty.

---

### Post by BUNTUNSE on 2008-04-12
:confused:Thanks for coming back to me.

Installation of Ubuntu is not a problem any more. I have actually installed Hardy Heron Beta as indicated in my earlier post.

My only predicament at the moment is to have the webcam, touchscreen, wifi and inbuild mic work. I have spent a lot of time to try and make any of these work, but have had no success. I am an immigrant from Windows Vista.

---

### Post by Lupus Umbrae on 2008-04-12
I got the WiFi working by using Ndis wrapper not the greatest way but appear to be the only way.

The touchscreen can be enabled but i only know how exactly for Ubuntu (7.10)

---

### Post by BUNTUNSE on 2008-04-12
:confused:
What is the code for wifi so that I can have a go again?

---

### Post by Lupus Umbrae on 2008-04-12
I've just noticed that i told you to put the drivers for the touch scrren in the wrong place. they need to go in the same place as the mosue drivers (usr/lib.xorg/modules/input for me)

use
```
find / -name mouse_drv.so
```
To find where you want to put it (should work)

I used synaptic package manager to get the graphics version of Ndis wrapper. I also get the wirelss drivers (finally found them) from [http://www.mediafire.com/?exuymodkstx](http://www.mediafire.com/?exuymodkstx)

Hope this works. If i get anything else working will let you know

---

### Post by BUNTUNSE on 2008-04-12
Hi,
Thanks for the lead.

'find / -name mouse_drv.so' returns 'permission denied'. Do I need to 'sudo' it?

Have downloaded the wireless drivers and put them in my 'Ndiswrapper' folder. Will explore with them.

---

### Post by BUNTUNSE on 2008-04-14
:confused:
Lupus Umbrae,

Thanks for your response. Can you kindly post for me the whole procedure, with codes that you used to get your wireless working?

Thanks in anticipation.

---

### Post by BUNTUNSE on 2008-04-14
Lupus Umbrae,

I have now tried your suggestion to get the touchscreen work, but I have had no success. I modified 'usr/lib.xorg/modules/input' to 'usr/lib/xorg/modules/input', and wrote '/TouchKit', even then I have no joy.

Furthermore, I have actually installed the 8.04 Alpha 6 64bit Beta of Ubuntu, using Wubi.

Do you have any more advice as I have not yet got touchscreen, wireless, webcam and microphone to work.

---

### Post by BUNTUNSE on 2008-04-16
:guitar:
Sorry for answering my own post. But I thought I needed to give everyone an update of success as I now have managed to get the wireless connection to the internet working. Thanks to the different posts in this forum and outside.

Here is what I did:
1. Downloaded the 'Ndiswrapper' (sources as suggested in ubuntu forum) to the desktop of my laptop (tx1340ea - running the beta version of ubuntu 8.04 Alpha 6)
2. Downloaded 'bcm4328.zip' (source as suggested in ubuntu forum) to the desktop of my laptop
3. Created a folder in the 'home' directory named 'jat' (you name it as you wish)
4. Created yet another folder in 'jat', namely 'ndiswrapper' (has got to be that (much easier to remember and to find the ndiswrapper related files)
5. Extracted the 'Ndiswrapper' contents (files) to my 'ndiswrapper' directory which I created in step number 4 above
6. I also extracted the contents of 'bcm4328.zip' into the 'ndiswrapper' folder or directory which I created in step number 4 above
7. Then, having earlier run or installed 'ndiswrapper' using 'Synaptic Package Manager' which is found under 'System, Administration'; I selected 'System, Administration', then at the bottom of the drop down list, I clicked 'Windows Wireless Drivers'. This brought me to a prompt for my password. 
8. Upon entering my password, then a small window opened titled 'Wireless Network Drivers'.
9. I clicked the 'Install New Driver' bar or folder icon (whichever the case might be on your laptop.
10. At this stage you must navigate or go to your 'ndiswrapper' folder you created and to which you extracted the two files or downloads above.
11. Select 'bcmwl5.inf
12. You will then be presented with the 'Wireless Network Drivers' window, hopefully with an icon in the box under 'Currently Installed Windows Drivers'. The Icon will have the text 'bcmwl5' and 'Hardware present: Yes' All that is left at this stage is for you to click 'Configure Network'.
Do the configuration, connect to the internet and join the information super highway again!

I now will try the touchscreen as suggested in the ubuntu forum.

---

### Post by BUNTUNSE on 2008-05-08
Hi there,

I am now running the Hardy Heron (Ubuntu 8.04LT) AMD64.

The wifi works fine, the touchscreen is okay, the audio is fine, although not the best since making the microphone work.

I now need help with two things. I need to make the tx1340 inbuilt webcam work. It is not recognised in Ekiga or Skype nor is it activated under multimedia.

I will also appreciate if anyone can help me get the finger print reader work.

Thanx a bundle.:confused:

---

### Post by Xhamanfla on 2008-05-10
Hey i done work the camera just installed "luvcview" and "cheese" with synaptic,  then you run cheese  and it works i have ubuntu studio 8.04....
 did you get the touchscreen work???? how?? im thinking that maybe the touchkit driver doesnt suport the xorg modules from 8.04

---

### Post by BUNTUNSE on 2008-05-10
Yes, the touchscreen works. I will get back to you with what to do as soon as I am back from my work over this weekend (probably Monday or Tuesday).:)

---

### Post by BUNTUNSE on 2008-05-10
By the way, thanks for the guidance regarding WEBCAM. I will try out your lead.

---

### Post by BUNTUNSE on 2008-05-13
Xhamanfla,

I followed this link to get my tx1340's touchscreen work:

[http://ubuntuforums.org/showthread.php?t=442483&page=87](http://ubuntuforums.org/showthread.php?t=442483&page=87)

I actually copied the code and pasted it into my configuration file. And surprise surprise, it worked.

As for your lead re: webcam, I installed the suggested via Synaptic Package Manager, but I still have no joy. The application works, but my webcam is not detected.

I am running MD64 Ubuntu 8.04 LTS version on the HP TX1340EA. If anyone has got a similar config, would you please help me with details of how you got the inbuilt webcam working? Cheers.

---

### Post by elsoda on 2008-05-18
Hi,
I am running AMD64 Ubuntu 8.04 LTS version 2.6.24-17 Kernel on the HP TX1340es

the installation by default works th Bluetooth fine but the WiFi card dosn't works, i must install Ndiswrapper and th bcm4328 driver and works fine right now.
i don't need install mouse support, this was detected fine by default

i try apply the code and driver for touch screen but this disable my keyboard, i make somthing wrong, tomorrow try again...

i don't try with the webcam and fingerscanner yet..

my question is, how i can do activate the quicklauch buttons? specially the rotate screen button..

thanks.

---

### Post by BUNTUNSE on 2008-05-21
Xhamanfla,

This is for your querry about touchscreen. I needed to be more specific.

If you look at gborzi's post here: [http://ubuntuforums.org/showthread.php?t=442483&page=89](http://ubuntuforums.org/showthread.php?t=442483&page=89).

Go to page 89, post number 890.

I copied the code in the box and pasted it in my xorg.conf file.

Better use  sudo emacs /etc/X11/xorg.conf in your terminal so that after you pasted the said text you can save the xorg.conf file.

After that you must ctrl+alt+backspace or restart the normal way.

You should be able to use your touchscreen capabilities with cellwriter.

I hope this is more specific.

Thanks to gborzi for sharing his/her work.:)

---

### Post by elsoda on 2008-05-25
BUNTUNSE:

i followed the thread instructions and it works! the tochscreens works, but how i can do calibrate and configurate the touch commands?

---

### Post by BUNTUNSE on 2008-05-26
I have not yet figured out how to succesfully do the calibration. After trying and failing a number of times I decided to take a break on trying since the touchscreen works fine for now and for the purpose of ordinary usage.

I hope you have installed cellwriter using Synaptic Package Manager. It is great for text entry. Absolutely.

---

### Post by BUNTUNSE on 2008-05-27
:)Hi fellows,

here is a success lead to hp pavillion tx1340ea (and possibly others) intergrated webcam installation. So far recognised with ekiga, not recognised yet with cheese. It worked on my lappy running hardy amd64.

Go to:
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation). On the page that opens, hit the link that is in the line saying, 'A tarball of the latest stable version is also available here (version 0.11.0).'

This will open the download dialogue for a "r5u870-0.11.0.tar.gz"

Make directory, say, "hpwebcam" under /home/[username]/ [username here being your $ name].

Drag and drop the downloaded tar.gz into the hpwebcam directory you created above, and extract it there using the best method you know.

Or extract by using "tar xvfz r5u870-0.11.0.tar.gz" (no quotation marks)

then, do cd r5u870-0.11.0

With root privileges give these commands,or just sudo as:

sudo make
sudo make install

and then the command:

sudo modprobe r5u870

If you want to make permanent the module loading on each boot, edit the file /etc/modules as follows: sudo emacs /etc/modules or use other text editor,then add, if these lines are not there already:

r5u870
videodev
video-buf
v4l1-compat
v4l2-common

save and close the file.

Also follow the instructions given under links 1 and 2 below for your webcam to work.

Reboot or restart X.

You open ekiga and use it!

For detailed info, go to my sources which are: 
1. http://wiki.mediati.org/Installation[/url]
2. [http://www.linuxquestions.org/questions/mepis-64/mepis-7.0-beta-5-installing-web-cam-driver-618983/](http://www.linuxquestions.org/questions/mepis-64/mepis-7.0-beta-5-installing-web-cam-driver-618983/)  (This is johnwick's post on LQ)

Credit to my sources.

---

### Post by LazyEngineer on 2008-05-28
To add to the thread - I have a TX1308.  It took a while and a lot of headaches to get Ubuntu working right.  But once you do, it's pretty neat.

Wireless was the hardest part for me.  Here's how I did it:
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)
Follow the original posters instructions carefully and it worked for me.

Audio may actually be working - try to play some music or something to check.  Ubuntu sometimes defaults to computer beeps for things - this doesn't mean your sound card isn't working.

---

