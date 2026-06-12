---
title: "Cant run Nvidia driver download!!!"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by vacman1 on 2007-09-06
Alright, gotta try linux again... so i just reinstalled feisty.

problem is i cant take this refresh rate anymore, and i cant seem to install the nvidia drivers that i downloaded

i have a geforce mx4000

when i type the command "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" like the nvidia page tells me to, it gives me this;

tim@tim-desktop:~$ sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
sh: Can't open NVIDIA-Linux-x86-1.0-9755-pkg1.run
tim@tim-desktop:~$ 

i tried the sudo command, but no help

feel pretty dumb here... but i'm very new to linux, so hopefully someone can tell me what stupid mistake i'm making

thanks!

---

### Post by rsambuca on 2007-09-06
Did you change to the folder with the file in it?

Also, just an FYI, but Feisty has a restricted Drivers Manager which will install it for you, if you wish.

---

### Post by vacman1 on 2007-09-06
not sure what all that means... what i have done since last post was right click the file, selected properties, selected permission tab, and checked allow executing file as a program.  now when i double click the file it extracts but then tells me i must be root...

now this root thing :(.... still trying to understand it... i logged into ubuntu with the username and password that i installed with, so how do i become root?  i tried using the sudo command in the terminal, but it gives me the same cant open file as before :(

---

### Post by rsambuca on 2007-09-06
Have you tried using the Restricted Drivers Manager?

Go to "System -> Administration -> Restricted Drivers Manager"

---

### Post by vacman1 on 2007-09-06
well once i did that a box came up... i checked enable for nvidia and it appears that ubuntu downloaded and installed everything... now going to reboot as required... lets see if it worked :)

thanks man!!!

---

### Post by Pumalite on 2007-09-06
Two more issues. Make sure you have build essential installed. Second: do this
sudo chmod 777 /path/to/driver/NVIDIA-Linux-xxx, then:
sudo sh /path/to/driver/NVIDIA-Linux-xxx
Accept license
Let the driver compile the modules
Let the driver reconfigure your xorg file
Then: sudo /etc/init.d/gdm start
And, if needed: startx

---

### Post by vacman1 on 2007-09-06
ok... didnt work ubuntu is telling me that it is running improper drivers b/c of the proprietry of the driver software...

what is build essential and how do i do that?

---

### Post by vacman1 on 2007-09-06
and is there certain #s that should replace those xxx's and how do i know which #s to use?  thanks

---

### Post by Pumalite on 2007-09-06
At the Terminal: sudo apt-get install build-essential
(It's needed to compile the modules)

---

### Post by vacman1 on 2007-09-06
tim@tim-desktop:~$ sudo chmod 777 /path/to/driver/NVIDIA-Linux-xxx
Password:
chmod: cannot access `/path/to/driver/NVIDIA-Linux-xxx': No such file or directory
tim@tim-desktop:~$ 
tim@tim-desktop:~$

---

### Post by vacman1 on 2007-09-06
ok setup the build essential still getting the file not found error... probably the xxx right? how do i know which #s to use for that?

---

### Post by Pumalite on 2007-09-06
xxx  are to be replaced by you depending on the driver you are using: example:
NVIDIA-Linux-x86-100.14.11-pkg1,run
NVIDIA-Linux-x86-100.14.09-pkg1.run
etc, etc

---

### Post by vacman1 on 2007-09-06
btw... a little crazy but after i went to the restricted drivers manager and enabled the nvidia settings, i now have sound!  i have a creative soundblaster sc :confused:

---

### Post by vacman1 on 2007-09-06
sudo chmod 777 /path/to/driver/NVIDIA-Linux-x86-1.0-9755 is what i used and;

tim@tim-desktop:~$ sudo chmod 777 /path/to/driver/NVIDIA-Linux-x86-1.0-9755
chmod: cannot access `/path/to/driver/NVIDIA-Linux-x86-1.0-9755': No such file or directory
tim@tim-desktop:~$ 
tim@tim-desktop:~$

---

### Post by Pumalite on 2007-09-06
Only you know where you put your driver; therefore /path/to/driver are to be replace by appropriate Path.

---

### Post by vacman1 on 2007-09-06
hmmmm.... i put it on my desktop, and i know im probably irritating you by now, but i'm really not sure what that path would be... i'm a dumb windows  user :) c:/windows/desktop   but i'm not sure what to use here.... ummm...

heck i dont even know what the drive is called :confused:

---

### Post by Pumalite on 2007-09-06
Move your driver to your /home and do this:
sudo sh /home/<yourname>/NVIDIA blah, blah, blah

---

### Post by vacman1 on 2007-09-06
man im feeling duuuumb... anyway looked at file properties and this is what i tried;

tim@tim-desktop:~$ sudo chmod 777 /home/tim/desktop/NVIDIA-Linux-x86-1.0-9755-pkg1.run
Password:
chmod: cannot access `/home/tim/desktop/NVIDIA-Linux-x86-1.0-9755-pkg1.run': No such file or directory
tim@tim-desktop:~$

---

### Post by Pumalite on 2007-09-06
If you moved your driver to /home, you don't need to put desktop in the middle.

---

### Post by vacman1 on 2007-09-06
sudo sh /home/tim/NVIDIA-Linux-x86-1.0-9755-pkg1.run

was the ticket... however 


  WARNING: The NVIDIA GeForce4 MX 4000 GPU installed in this system is         
           supported through the NVIDIA 1.0-96xx legacy Linux graphics         
           drivers.  Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for   
           more information.  The 1.0-9755 NVIDIA Linux graphics driver will   
           ignore this GPU.

---

### Post by Pumalite on 2007-09-06
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by vacman1 on 2007-09-06
last time i'll bother you and then i'll bite the bullet if i cant get it to work... but which driver do i select from that webpage?

---

### Post by Pumalite on 2007-09-06
Try both 'Legacy Drivers'. See which one works.

---

### Post by vacman1 on 2007-09-06
wow! this got too complicated for me... i cant follow the instructions on the nvidia website to install this driver... cant figure out how to run % makefile install from the extracted directory heirechy, and that's the easy part... why is this so complicated?  damn... this is why i went back to windows (which sucks) last time.... anyway guess im just a little discouraged but i certainly appreciate all your help... suppose i'll keep tinkering here and see if i can figure it out

---

### Post by Pumalite on 2007-09-06
The fun of Linux is that you can tinker with it and everyday you know a little more.

---

### Post by vacman1 on 2007-09-06
yeah i just wanted to get this driver installed so i could stand looking at this screen... to start learning linux... definately had more patience for this when i was 12 and taught myself basic!  

of course the nagging wife bitching about being on the comp doesnt help :) how things have changed.... lol

---

### Post by Pumalite on 2007-09-06
Growing up is hard.

---

### Post by vacman1 on 2007-09-06
alright one last time....

here are the instructions;

Chapter 1. Installing the NVIDIA Driver

This installation procedure will likely be simplified further in the future, but for the moment you will need to download the NVIDIA FreeBSD Driver Set archives from the NVIDIA website, extract them to a temporary location of your choice, and run the following from the root of the extracted directory hierarchy:

    % make install

i downloaded the file, extracted it to home but cannot get it work... tried extracting to other places as well.... what the heck am i doing wrong here?;

here i am trying to get to the root folder of the extracted file to run the above command, but as you can see it tells me that there is no such directory... but there is

tim@tim-desktop:~$ cd /home
tim@tim-desktop:/home$ cd /tim
bash: cd: /tim: No such file or directory
tim@tim-desktop:/home$ cd /desktop
bash: cd: /desktop: No such file or directory
tim@tim-desktop:/home$ 

so i have tried everything i can think of, including this;


tim@tim-desktop:/home$ % make install
bash: fg: %: no such job
tim@tim-desktop:/home$ cd ..
tim@tim-desktop:/$ % make install
bash: fg: %: no such job
tim@tim-desktop:/$ cd /home
tim@tim-desktop:/home$ % make install NVIDIA-FreeBSD-x86-1.0-9639.tar.gz
bash: fg: %: no such job
tim@tim-desktop:/home$ cd ..
tim@tim-desktop:/$ % make install NVIDIA-FreeBSD-x86-1.0-9639.tar.gz
bash: fg: %: no such job
tim@tim-desktop:/$ 

and this;

tim@tim-desktop:/$ % make install /home/tim/desktop/NVIDIA-FreeBSD-x86-1.0-9639
bash: fg: %: no such job
tim@tim-desktop:/$ 

and plenty more but i dont want to clog this forum up with my garbage... lol

thanks again

---

### Post by rsambuca on 2007-09-07
I understand your frustrations, as it can be quite confusing at the beginning.  One thing that is critical to understand here is that in linux, the filenames and folder names are case sensitive.  Thus desktop will not get you to your Desktop!

---

### Post by vacman1 on 2007-09-07
tim@tim-desktop:/$ % make install /home/tim/desktop/NVIDIA-FreeBSD-x86-1.0-9639
bash: fg: %: no such job
tim@tim-desktop:/$ cd /home/Tim/Desktop
bash: cd: /home/Tim/Desktop: No such file or directory
tim@tim-desktop:/$ cd /home
tim@tim-desktop:/home$ cd /Desktop
bash: cd: /Desktop: No such file or directory
tim@tim-desktop:/home$ cd /Tim
bash: cd: /Tim: No such file or directory
tim@tim-desktop:/home$ cd /tim
bash: cd: /tim: No such file or directory
tim@tim-desktop:/home$ cd /
tim@tim-desktop:/$ cd /home/tim/Desktop
tim@tim-desktop:~/Desktop$ % make install
bash: fg: %: no such job
tim@tim-desktop:~/Desktop$ make install
make: *** No rule to make target `install'.  Stop.
tim@tim-desktop:~/Desktop$ % make install/NVIDIA-FreeBSD-x86-1.0-9639
bash: fg: %: no such job
tim@tim-desktop:~/Desktop$ $ make install NVIDIA-FreeBSD-x86-1.0-9639
bash: $: command not found
tim@tim-desktop:~/Desktop$ cd NVIDIA-FreeBSD-x86-1.0-9639
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % make install
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ make install
Makefile:20: *** missing separator.  Stop.
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % install
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ install
install: missing file operand
Try `install --help' for more information.
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ make
Makefile:20: *** missing separator.  Stop.
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % make install
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % makefile install
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % makefile
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % make install makefile
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % install makefile
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ % install
bash: fg: %: no such job
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ %
bash: fg: %: no such job

arggggggg

---

### Post by rsambuca on 2007-09-07
Once you are in the nvidia folder, you need to enter```
sudo make install
```Then enter your password at the prompt

Also, I hate to tell you this but it looks like you downloaded the wrong driver.  freeBSD is a different OS alltogether.

---

### Post by vacman1 on 2007-09-07
that's what i thought... but the  pumalite told me to try those 2 :confused:


tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$ sudo make install
Password:
Makefile:20: *** missing separator.  Stop.
tim@tim-desktop:~/Desktop/NVIDIA-FreeBSD-x86-1.0-9639$

---

### Post by vacman1 on 2007-09-07
excuse my ignorance i know this is x86 ubuntu, or is it IA32?

man i'm all confused :(((

which of these should i use?

Linux IA32
Latest Version: 100.14.11
Latest Legacy GPU version (1.0-71xx series): 1.0-7185
Latest Legacy GPU version (1.0-96xx series): 1.0-9639
Archive

Linux IA64
Latest Version: 1.0-5336
Archive

Linux AMD64/EM64T
Latest Version: 100.14.11
Latest Legacy GPU Version (1.0-71xx series): 1.0-7185
Latest Legacy GPU Version (1.0-96xx series): 1.0-9639
Archive

FreeBSD x86
Latest Version: 100.14.11
Latest Legacy GPU Version (1.0-71xx series): 1.0-7185
Latest Legacy GPU Version (1.0-96xx series): 1.0-9639
Archive

Solaris x64/x86
Latest Version: 100.14.11
Latest Legacy GPU version (1.0-96xx series): 1.0-9639
Archive

---

### Post by rsambuca on 2007-09-07
You want the Linux IA32
Latest Legacy GPU version (1.0-96xx series): 1.0-9639

---

### Post by Perfect Storm on 2007-09-07
Ignore the previous in this thread;

Go to Nvidia page and download the LINUX legacy version of the driver (Linux IA32) to your Desktop:

```

sudo nano /etc/default/linux-restricted-modules-common
```

change **DISABLED_MODULES=""** to **DISABLED_MODULES="nv"**

save (ctrl) + (o) and exit (ctrl) + (x)

```
cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh <name of the file>
sudo /etc/init.d/gdm start
```

and you're done.

NOTE: *sudo /etc/init.d/gdm stop* will take you out of X and you'll be in commandline. So print the instructions out.

---

### Post by vacman1 on 2007-09-07
dude you're freaking awesome!!

it's actually working up till this point;

tim@tim-desktop:~/Desktop$ sudo rm /etc/init.d/nvidia-*
rm: cannot remove `/etc/init.d/nvidia-*': No such file or directory
tim@tim-desktop:~/Desktop$ 
tim@tim-desktop:~/Desktop$

ok... think i have to enter the nvidia file where u put the asterik right? and then the <filename> in the next command is the same/

---

### Post by Perfect Storm on 2007-09-07
Just continue, the sudo rm /etc/init.d/nvidia-* is just a safty that everything is gone from previous attempt.


other question, answer:

eg.

sudo sh NVIDIA-Linux-x86-1.0-7185-pkg1.run


when out of X, the comand;

dir

will be useful to check the name of the file.

---

### Post by vacman1 on 2007-09-07
wow awesome man! thanks alot!

had a little problem when i exited gui... umm X right?  anyway just gave me a cursor so i pressed  cntrl-alt-bkspce and  then it worked from there... screen looks a little better. is there a way i can test to see if the driver and video card are performing correctly?

anyway, i have no idea what exactly i did, but one thing is for sure, nvidia needs to put what you just gave me on their website instead of five pages of craziness that i sure couldn't understand!

i saved the terminal window and the code you gave me, and hopefully with that and the info on the nvidia website i can learn what i actually did there... lol

thanks again!!!
:guitar:


one more quick ?
now when i goto restricted drivers manager it tells me i have to install linux restricted modules.... is this normal? it worked before... is that b/c the nvidia driver was restricted since it wasn't installed properly?



OUCH! ... ummm maybe i still have a problem... my refresh is set to 50 Hz now... i use 75-85 in XP.   it gives me the option to go up to 58 but that tweaks the screen out.... hmmm

---

### Post by Perfect Storm on 2007-09-07
Did the Nvidia logo showed up when entering?

a little test:

```
glxgears
```

---

### Post by vacman1 on 2007-09-07
no logo, but i can see the gears

tim@tim-desktop:~$ glxgears
5673 frames in 5.0 seconds = 1134.529 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
tim@tim-desktop:~$


maybe i should try the other (there were 2) version of the driver?

---

### Post by Perfect Storm on 2007-09-07
try test it on some off the 3D screensavers for sure.

---

### Post by vacman1 on 2007-09-07
well i can see the 3d images, but the quality isn't great... do you think i should have a higher refresh rate?  do you think i should try to install the other legacy driver? thanks

---

### Post by Perfect Storm on 2007-09-07
Lets see;

```
cat /etc/X11/xorg.conf
```

Which version of the legacy did you install?

---

### Post by vacman1 on 2007-09-07
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Compaq  V70"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 125.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 4000"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1024x768_85 +0+0; 1024x768 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


there were two versions of the IA32 legacy drivers... i installed the 9639.pkg1

however since last post i found a thread and used;

sudo nvidia-settings

there i changed the refresh rate and now ubuntu gives me 97Hz!  I don't think this is correct... lol... the screen does look a little better though :)

sorry... changed the refresh in the nvidia settings from 75 to 85Hz

---

### Post by vacman1 on 2007-09-07
btw you rock man!  i'm checking out your webpage and am installing beryl... i want that awesome gui!!! lol

wow man... im never going back to windows!

---

### Post by Perfect Storm on 2007-09-07
Just be careful when playing around with the refresh rate.

Here's a tips;
If X(gui) fail to load because of beryl/driver/other

then when in CLI;

sudo nano /etc/X11/xorg.conf

and change the driver "nvidia" to "vesa" to get X back.

---

### Post by Perfect Storm on 2007-09-07
show off of beryl: [http://www.youtube.com/watch?v=bYsxaMyFV2Y](http://www.youtube.com/watch?v=bYsxaMyFV2Y) (requires flash)

Beryl howto: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)

My tips'n'tricks eyecandy: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by vacman1 on 2007-09-07
thanks for the tip!

and yeah i think i burned up my other monitor b/c of refresh, even though i didn't change it that time (my last experience with linux)

anyway, i've installed beryl (had no idea what it was until i installed it...freaking sweet!) and downloaded the desktop mod of yours, but i cant seem to load it into beryl.  i double click it and even typed in beryl-manager to open it, but doesn't seem to work so far.

---

### Post by Perfect Storm on 2007-09-07
Did you also select it?

---

### Post by vacman1 on 2007-09-07
ummm.... select it how?

edit...i'm still reading the rest of your page...

but when i minimize a window it glitches a little (hangs up at the bottom of the tasbar) before minimizing...is this normal with beryl?

i gotta ask man... do you do this for a living? if not you should definately make an assload of money for your work.  those themes i've seen so far smoke anything windows has ever put out!  heck one of the biggest turn offs for ubuntu for me is that ugly brown gui....lol

---

### Post by Perfect Storm on 2007-09-07
Try add this to your sourcelist:


```
sudo nano /etc/apt/sources.list
```

add:

[b]### Compiz Fusion ###
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
[/b]

Save (ctrl) +(o) exit (ctrl)+(x)

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install beryl emerald-themes beryl-manager
sudo nano /etc/X11/xorg.conf
```

check if **Option "AddARGBGLXVisuals" "True"** is under **Section "Device"**

---

### Post by Perfect Storm on 2007-09-07
> **vacman1 said:**
> ummm.... select it how?

i gotta ask man... do you do this for a living? if not you should definately make an assload of money for your work.  those themes i've seen so far smoke anything windows has ever put out!

I use my sparetime, it's a hobby of mine. All the help on this board is done by people for free (in the spirit of Ubuntu/Open Source)

I work in a daycare center normally.

---

### Post by vacman1 on 2007-09-07
those kids have an awesome teacher.

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 4000"
EndSection
 

not listed

and i cant find the themes folder

---

### Post by Perfect Storm on 2007-09-07
Then add

Option **"AddARGBGLXVisuals"   "True"**    to that section so it looks like this

(taken from my xorg.conf)

[b]Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
EndSection
[/b]

To make beryl start up everytime you boot-up:

```
gnome-session-properties
```

Press new, and add;

**beryl-manager**

as command

---

### Post by Perfect Storm on 2007-09-07
Try this one (theme) instead;

Unpack (Extract here) first.

---

### Post by vacman1 on 2007-09-07
ok haven't done that yet, but somehow my top taskbars went flat and now i have to hold alt to drag them, before i could drag them with the mouse

ok adding those commands now

yeah i've lost the close, minimize buttons...etc.

---

### Post by Perfect Storm on 2007-09-07
*You need to restart before the new command you put in xorg can take affect, that's why you can't see it.

---

### Post by vacman1 on 2007-09-07
i restarted but i still dont have the buttons, and i cant drag the windows

and the little pop windows on the bottom are almost white... hmmm what did i do...

---

### Post by Perfect Storm on 2007-09-07
Can you post a screenshot of what you mean?

---

### Post by vacman1 on 2007-09-07
here's the screenshot... i think... lol

attachment

---

### Post by Perfect Storm on 2007-09-07
ok first to fix so you have normal borders back:

right click on the beryl icon (next to the volume) and select windows manager back to Metacity.

---

### Post by vacman1 on 2007-09-07
ok done

---

### Post by Perfect Storm on 2007-09-07
```
sudo /etc/init.d/gdm stop
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
```

Hope it works.

---

### Post by vacman1 on 2007-09-07
first line of cod crashed the gui

---

### Post by Perfect Storm on 2007-09-07
press <ctrl> +<alt> +<F1> first

---

### Post by Perfect Storm on 2007-09-07
By the way which version of the legacy did you choose?

---

### Post by vacman1 on 2007-09-07
5936

entering code now

ok code entered...seems to be successful... everything looks the same (standard)

ummm it was the NVIDIA-Linux-x86-1.0-9639-pkg1.run

---

### Post by Perfect Storm on 2007-09-07
I'm not sure about this but I think only 9639 and above can use beryl.

---

### Post by vacman1 on 2007-09-07
yeah sorry i was going off memory... it was actually 9639

edit... should i go back to beryl now?

---

### Post by Perfect Storm on 2007-09-07
ok

---

### Post by vacman1 on 2007-09-07
tried beryl... the borders are translucent... and they're going up into the taskbar... it's no that the buttons are missing

---

### Post by Perfect Storm on 2007-09-07
in the panel below, right click on the window and choose **Move**

---

### Post by vacman1 on 2007-09-07
ok im in beryl i clicked move and i can drag the windows to distort them, and the upper border is brown but still a little translucent
also the words in the little popups on the bottom are not readable like before

attachment



but if i maximize the page the border goes back up into the taskbar... or maybe the buttons just disappear...not sure

---

### Post by vacman1 on 2007-09-07
attachment

---

### Post by vacman1 on 2007-09-07
ok so i managed to load your theme and it seems to be working fine except it doesn't really look like your theme

---

### Post by vacman1 on 2007-09-07
2. Make sure that gtk2-engines-pixbuf is installed (a quick search in synaptic if you're in doubt if it's installed).

dont seem to have this.. how do i get it?

---

### Post by Perfect Storm on 2007-09-07
```
cat /etc/apt/sources.list
```

---

### Post by vacman1 on 2007-09-07
yeah im lost there... not sure what to do

---

### Post by Perfect Storm on 2007-09-07
Your sourcelist is properly not set up correctly (enable univer/multiverse/mediaubuntu)

---

### Post by vacman1 on 2007-09-07
bash: enable: univer/multiverse/mediaubuntu: not a shell builtin
tim@tim-desktop:~$ enable univer/multiverse/mediaubuntu
bash: enable: univer/multiverse/mediaubuntu: not a shell builtin
tim@tim-desktop:~$

---

### Post by vacman1 on 2007-09-07
really wish i new what i was doing wrong here... downloaded vendetta and when i type the command the webpage gives me, tells me it cant find file... hmmm what have i done...

---

### Post by Perfect Storm on 2007-09-07
```
sudo nano /etc/apt/sources.list
```

Now erease it all and replace it with mine. Here's mine;

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

### Ubuntu supported packages
### GPG key: 437D05B5
deb http://dk.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://dk.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

### Ubuntu community supported packages
### GPG key: 437D05B5
deb http://dk.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://dk.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

###############################
##### UNOFFICIAL SOURCES ######
###############################

### Seveas' Ubuntu Packages
### GPG key: 1135D466
deb http://mirror.ubuntulinux.nl/ feisty-seveas all 
deb-src http://seveas.theplayboymansion.net/seveas feisty-seveas all

### Ubuntu backports project
### GPG key: 437D05B5
deb http://dk.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 
deb-src http://dk.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

### Upstream Wine
### GPG key: 387EE263
deb http://wine.budgetdedicated.com/apt feisty main 
deb-src http://wine.budgetdedicated.com/apt feisty main

### Upstream Beryl
### GPG key: ed8a569e
#deb http://ubuntu.beryl-project.org/ edgy main-edgy 
#deb-src http://ubuntu.beryl-project.org/ edgy main-edgy

### Medibuntu multimedia packages
### GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

### Canonical Commercial packages ###
### GPG key: 437D05B5
deb http://archive.canonical.com feisty-commercial main 
deb-src http://archive.canonical.com feisty-commercial main

### Compiz Fusion ###
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

## Cinelerra for P4 ###
# deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/ ./

```

Note, where it says **dk**, you might change it to your land code.
save and exit.

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install gtk2-engines-pixbuf
```

Note: You have now alot of stuff available to download throufh synaptic package manager. (system ---> Adminstration ---> Synaptic Package Manager.


Vendetta:

If the file is on Desktop;

```
cd ~/Desktop
sudo sh <Vendetta-file>
```

When installed, exit the installer.
Note; with script installation (.sh/.run files) especially games you need to exit the installer, don't hit launch/play as it would mess up the permission system of that game If you install it it system-wide (the sudo thing).

Also note everything that is not install as a .deb (ubuntu packages) will not shown up in apt-get/aptitude/synaptic and might not be easely uninstalled.

---

### Post by vacman1 on 2007-09-07
thanks for all your help man!

got things looking pretty good now (screenshot), but more importantly i learned a ton of stuff just doing all of that... definately much more to learn :)

anyway i've somehow lost sound during this process... so that's my next adventure

can't wait to show this desktop to my die hard windows friends!

---

### Post by Perfect Storm on 2007-09-07
My pleasure.

Sound stuff isn't my speciality, but might be a good idea to search or start a new  thread for that.


regards
A.I. Dude

---

### Post by Perfect Storm on 2007-09-07
By the way you might try out kiba-dock:

```
sudo aptitude install kiba-dock kiba-plugins-gnome kiba-plugins kiba-settings
```

You can start it via Accessories. It might be a little unstable (alpha software), but it's damn cool. Works best when beryl is running, and you can configure it like crazy.

---

