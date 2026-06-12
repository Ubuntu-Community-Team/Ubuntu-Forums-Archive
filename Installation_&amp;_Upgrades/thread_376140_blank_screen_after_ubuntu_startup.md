---
title: "blank screen after ubuntu startup"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by lttmik on 2007-03-04
screen goes blank after unbunto starts Ive run it in every way inmaginable and i get nothing always the same starts up fine but after load screen goes away nothing comes up any ideas?

---

### Post by taurus on 2007-03-04
What's the spec of your machine especially your graphic card?  Can you get into a console with <Ctrl><Alt>F2?  Log in and reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Just use the default value if you are not sure about a question and use **vesa** as a driver for your graphic card.  Save it and reboot and see if X is working this time.

```
sudo shutdown -r now
```

---

### Post by lttmik on 2007-03-04
when would i hit alt cntrl f2?

---

### Post by lttmik on 2007-03-04
my graphics card btw is a radeon 9800 pro 256mb

---

### Post by taurus on 2007-03-04
Wait for it to finish booting, after screen goes blank.

---

### Post by lttmik on 2007-03-04
i do this nothing happens the only thing i can do is a hard reboot

---

### Post by taurus on 2007-03-04
Okay, boot into recovery mode from the GRUB menu and at the prompt, run

```
dpkg-reconfigure xserver-xorg
```
And when you are done, reboot it with

```
shutdown -r now
```

---

### Post by lttmik on 2007-03-04
it says my syn is out of range? after i load

---

### Post by lttmik on 2007-03-04
im still getting nothing

---

### Post by taurus on 2007-03-04
Look at the manual for your monitor to see what are the values for vertical and horizontal refreshing rates.  Then, pick them from the list or type them in yourself when you run that command again in the recovery mode.

---

### Post by lttmik on 2007-03-04
im still getting a blank screen hey when i go through all that stuff at one point it asks me to pick the monitor sizes should i jst do simple for it because the H and V are default is there any other reason its doing this?

---

### Post by lttmik on 2007-03-04
ok maybe this is my problem it asks 

configuring x server -xorg
video card's bus idetifier:

PCI:1:0:0

does this look like its right or should i be typing something in here?

---

### Post by lttmik on 2007-03-04
another thing a couople of the things look like this:

[*] bitmap 

theres a bunch of them in a vertical row and when i hit the down arrow key it turns into

[** bitmap

wat exactly is it doing because for this one its asking for this:

x.org server modules that should be loaded as defaults does that mean i should be going down the line so that they all look like:

[** bitmap

it also does this for how big i wnt the reeolution set to.

---

### Post by lttmik on 2007-03-04
can anyone help me with this?

---

### Post by taurus on 2007-03-04
What's the output of this command?

```
lspci
```

---

### Post by lttmik on 2007-03-04
displays a bunch of information deling with mass storage controllers, raid bus controller, ide interface, usb controller, isa bridge, vga compatible controller: ati technologies inc radeon r350 radeon 9800, and display controller:L ati technologies inc readeon r350 radeon 9800 pro
tell me if u really wnt me to type the whole thing out i will.

---

### Post by lttmik on 2007-03-04
Do you guys think that im having the same problem if so how do i do what he did?

Hello,
a week ago I had upgraded my well running 6.06 to 6.10, online, onto Laptop AcerTM22420.
Well, the 6.06 was running fine before, now I had sorted out a few problems on 6.10, but still encountering problems with gnome and gdm.
Browse through a lot of pages, find that a lot of users seem to have similar problems, like "can not run gdmsetup",
getting error messages like 
"Failed to connect to socket, sleep 1 second and retry
Trying failed command again. Try 2 of 5."
and other gnome / gdm login problems

Now I found on this page :
[https://launchpad.net/ubuntu/+source/gdm/+bug/66034](https://launchpad.net/ubuntu/+source/gdm/+bug/66034)

And guess what, with a simple 
# mv S13gdm S21gdm
as user root in the /etc/rc2.d/ directory,
ALL is working fine for me now. (.gdm_socket is present in the /tmp)

I understand, now the gdm is started somewhat later than other processes on the bootup.

Hope this finding might help others, please leave a short note if it did.

Greetings from Germany

Wolfgang

---

### Post by lttmik on 2007-03-04
no one knows wats wrong?? hasn't anyone had this problem before?

---

### Post by BMWolfgang on 2007-03-04
Hi,
have you by chance ever tried to configure your x-server.
dpkg-reconfigure xserver-xorg

To get an idea about my video settings, I had the "other operating system" up to give me more info about it.

Good luck

Wolfgang

---

### Post by lttmik on 2007-03-04
I did indeed do this do you think i could pm u about this problem maybe u can help me fix it I just wnt it to stop giving me  a blank screen after it gets done loading.

---

### Post by BMWolfgang on 2007-03-04
sorry, I am on a boat and we have bad satellite connection.

Whatever means of communication is convenient. I will be up the next 3 hours from now.
But I am also limited with my knowledge.
I understand, the x-server does start automatic, or do you manually use startx.
And what happens if you use crtl-alt-backspace when the x had started.
I know, this has been proposed before, reinstall x-org or gdm

---

### Post by lttmik on 2007-03-04
what do u mean reinstall those things and when would i hit ctrl alt spacebar? after it goes blank?

---

### Post by BMWolfgang on 2007-03-04
to try to reinstall the x-server, go to your ctrl-alt-F1 and 

sudo dpkg-reconfigure xserver-xorg

this might help.

When xserver is running, a ctrl-alt-BACKSPACE, not spacebar should normally stop the xserver and bring your display either back to your login screen, whether it was the terminal or the login-window.


if the reinstall of x-org did not help, try 

sudo dpkg-reconfigure gdm

then I would try my finding which you mentioned earlier, actually, try to go to the reference bug page and get an idea, try to find the .gdm_socket   file in /tmp

---

### Post by c500 on 2007-03-05
Thanks if I may join this - I have gone through the reconfiguration but now at the end end I get a line of code root@500-laptop:~#

What do I do?

---

### Post by BMWolfgang on 2007-03-06
if I understand this correctly, yours is booted and you are logged on as root (the hash #), should not start the xserver as root, but try to type

startx

if you are root, you would want to create a new user

---

