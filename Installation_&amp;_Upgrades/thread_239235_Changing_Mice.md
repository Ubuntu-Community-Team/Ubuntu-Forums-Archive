---
title: "Changing Mice"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Surf Man on 2006-08-18
I have a two button Mirco Mouse that worked fine after install. I tried to change to a three button mouse and it will not respond. Any suggestions on how to fix this. Thank you](*,)

---

### Post by zxee on 2006-08-18
When you change hardware on debian anyway you will need to run reconfigure.
Did you change from ps2 to usb mouse?
Open a terminal i.e Applications>Accessories>Terminal and type > sudo dpkg-reconfigure xserver-xorg That command runs a program to edit your xserver (basically) so pick the correct mouse for what your using and just press enter for questions you don't know.

---

### Post by Surf Man on 2006-08-19
Thank you very much. I want to use both eventually actually, the cheap three button generic I am wanting to add and next the logitech. I have one I use on laptop.

My goal for today is to install and use that blanking mouse 8) 

So it appears that the command will autodect the hardware and hopefully make device usable. What would be the next step if that doesn't work? 

I am guessing you would go in and manually add in variables, as described in the guide for logitech mouse. I am still sketchy on editing but got the idea that adding # in front of the old command lines instead of erasing was a good move in case you had to go back. Is there a place with specific variables and scripts to paste for types of devices? I couldn't get a list of my devices using the "cat/proc/bus/input/devices" command. I added sudo and still got invalid file error. Do I add cd or sudo in front of that? Thanks again and kindest regards.

---

### Post by Surf Man on 2006-08-19
I entered the command and it sent an error message that the package wasn't installed. How do I install this package? Thanks.

---

### Post by zxee on 2006-08-19
sudo in front of commands allows you root privledge.
> I entered the command and it sent an error message that the package wasn't installed. How do I install this package? Thanks.
Reply With Quote 
I need to have clarity here in order to be helpful. 
What exactly did the terminal output from the sudo dpkg-reconfigure...
command? It's highly unlikely that you don't have dpkg installed but maybe?? 
What version of ubuntu are you using? If you don't know type > lsb_release -a or copy and paste that command into a terminal.

---

### Post by Surf Man on 2006-08-19
The error message I got was.
Package 'xserver-org' is not installed and no info is available.
Use dpkg--info(=dpkg-deb--info) to examine archive files, and
dpkg--contents(=dpkg-deb--contents) to list contents
/user/sbin/dpkg-reconfigure:xserver-org is not installed


When I put in the lsb_release-a I got the command not found error. 

I installed the latest alternate 6.06 i386 version from Ubuntu site.

I can do a fresh install if needed. What do you think my friend?

---

### Post by zxee on 2006-08-19
Hi, I think that you don't have an xserver. Did you download the server version? If you didn't did you check the md5sum of the iso before burning?
Sorry for all the questions but it's how I collect the pieces to this puzzle.  
Are you using a window manager-which one? or are you doing everything from commandline. I don't know how you could not have an xorg and be using a mouse or windowmanager?
You did enter the command with the sudo? i.e > sudo dpkg-reconfigure xserver-xorg ??

---

### Post by Surf Man on 2006-08-19
I re entered the command and got into the xserver screen and followed your advice about hitting enter if not sure. I went through the autodect section and it gave me two options for the mouse and I noticed it said that the configuration tool did not support the scrolling wheel type mice. I tried it with both options for mouse selection and both options for button emulation and it still is a no go. What now. The mouse I have has the scroll wheel and would be five button right? I am going to go surfing and will check back in a few hours. Thank you for your patience. I must have not typed in the command properly on the first attempt.

---

### Post by Surf Man on 2006-08-19
:-D I got it going by replacing it with a logitech mouse and it is working fine. Thanks for your help, I learned a lot. Kindest Regards.

---

### Post by zxee on 2006-08-20
Glad it's working for you now.

---

