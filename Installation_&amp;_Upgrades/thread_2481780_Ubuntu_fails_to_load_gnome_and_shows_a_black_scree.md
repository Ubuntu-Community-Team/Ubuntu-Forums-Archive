---
title: "Ubuntu fails to load gnome and shows a black screen on boot"
date: 2022-12-08
forum: Installation &amp; Upgrades
---

### Post by cwoelfle on 2022-12-08
I was working on a company laptop implementing stigs on a ubuntu workstation. I updated things like the max password lenth, minimum password length, and added a banner. After a systemctl restart gdm.service the restart failed and everytime I boot I get a black screen that show the drive name follow by a kauditd overflow message on several lines below it like so:

/dev/nvme0N1p2: clean xxxxxxxx / xxxxxxx files xxxxxxx / xxxxxx blocks

[    xx.xxxxxx ] audit: kauditd holq queue overflow
[    xx.xxxxxx ] audit: kauditd holq queue overflow
[    xx.xxxxxx ] audit: kauditd holq queue overflow
[    xx.xxxxxx ] audit: kauditd holq queue overflow
[    xx.xxxxxx ] audit: kauditd holq queue overflow

I can access the vtys so I attempted a gnome restart by using the following

sudo systemctl restart gdm.service

it failed and told me to use journalctl -xe, when I used that command I got 3 red rows of errors:

failed to load gnome display manager

failed to start detect the available GPUs and deal with any system changes


barriers:

I have an install usb drive to install fresh, but there is important software on the system that I need to get off before I can do a fresh install. This is my last stand if I cant manage to figure it out from help on here.

The system does not have access to the public internet so apt install an resinstalls is not possble unless I can download the packages, put them on the usb, and install from the usb.


does anyone have any advice on where I could start? or is setting up a backup drive and performing a fresh install the only way to get my system back to running while keeping the files we need intact?

---

### Post by MAFoElffen on 2022-12-08
Start by booting from your USB LiveCD media and do a backup of what is there... Get to your data. That is the important part right?

Do that before trying to rescue it. 

From there, run an[ UbuntuForums "system-info" script]("https://github.com/UbuntuForums/system-info") so we know what we are working with and recommending options for...

---

### Post by cwoelfle on 2022-12-09
I cant use wget because the system is not connected to the public intenet and is only allowed to run on lan. How would I go about putting that on a usb to run it?

---

### Post by tea for one on 2022-12-09
On the GitHub page, there is a [COLOR="#0000FF"]Download the script[/COLOR] link (under Run from GUI).

---

### Post by MAFoElffen on 2022-12-09
> **cwoelfle said:**
> [COLOR=#ff0000]I have an install usb drive to install fresh[/COLOR], but there is important software on the system that I need to get off before I can do a fresh install. This is my last stand if I cant manage to figure it out from help on here.

You said the above... If you have the above, then you could boot from it and see if you can get an internet connection by using it... and how it is configured. If you can, then that would tell us a lot in what might be wrong with your current circumstances... and how it is configured.


Is your laptop usually connected via a wireless connection or a wired connection? For instance is there any connection to the internet at your home? Describe how you would connect to the internet before there was a problem...

---

### Post by MAFoElffen on 2022-12-09
Let me back up a few to tell you what is going on in my head as I read your first post... From what you said, it boots to a black screen, which would mean the graphics layer is somehow not getting you to a graphical logon screen. Is that a fair assessment so far? You posted some text of a sampling of what you see on your screen, so it is "not always black/blank" right? Which those messages could be many various things...

The first could just be that you are turning off your computer without shutting it down correctly (turning off the switch) so it just has orphaned inodes from a cold, immediate shutdown... That it is dong it's job in cleaning up on a restart after something like that.

You say that you can get to your vtty sessions (text/console based), so the kernel is booting successfully, just not the graphics layer. You got that far, so I am assuming you have at least some computer skills to get that far. That also tells me that your computer does get to a certain point... All hope is not lost. Your computer does work to a certain stage... It just seems to have a configuration problem.

It is hard for me to see what is happening on your computer, unless you paint a picture for me to see what you see, and what is going on. If you can take pictures or videos to show what is going on, that will help.

You said this was a work computer. Does that mean it was being used for work? Or provided by your work? Or is this your own personal computer? Does your work have a Technical Support?

Please help me to be able to help you...

---

### Post by cwoelfle on 2022-12-09
I downloaded the file, performed a chmod -x to give it execute permission, and ran it but it gives me an error.

I ran ls to make sure the file was there and it shows system-info in my home directory so I execute the following:

./system-info but it gives me the following error:

bash ./system-info /bin/bash^M: bad interpreter: no such directory or file

Also attemtped removing .txt from the end and changing the extension to .sh and performing the same operations as above with 2 additional runs shown below:

sh ./system-info.sh

bash ./system-info.sh

Same error as above.

---

### Post by tea for one on 2022-12-09
A file in your home directory called system-info.txt is usuallly the result of running the script.

---

### Post by MAFoElffen on 2022-12-10
As tea for one said, the script file is called "system-info". The report is creates is 'system-info.txt'. 

What I usually do is to either down it to the Downloads directory, or create a ~/Scripts directory, and change directory to it, before downloading the script, so there is no confusion where the scripts reside, and which file is the report.

That script is a Bash Script, which means after it is changed to being executable, that it is executed while in the same directory via
```

[COLOR=#ff0000]./[/COLOR]system-info

```
meaning: [COLOR=#ff0000]current directory,[/COLOR] execute this command...

If you were in the same directory and just typed "system-info" it would get an error saying "command not found", that would indicate that you didn't type "./" to tell it it is in the current directory.

If you typed 
```

bash ./system-info

```
It would start an additional bash shell, within a bash shell, but it would still start.

But you said you got this error:
```

bash ./system-info /bin/bash[COLOR=#ff0000]^M[/COLOR]: bad interpreter: no such directory or file

```
Which tells me you downloaded the script from a Windows OS machine... Which adds a carraige return at the end of each line of the script and confuses the BASH interpreter...

To fix the existing script (by removing those added extraneous characters), do
```

sed -i -e 's/\r$//' system-info
./system-info

```
OR
```

sed -i -e 's/^M$//' system-info
./system-info

```
OR... download the script from a Linux machine or Linux LiveCD media...

---

