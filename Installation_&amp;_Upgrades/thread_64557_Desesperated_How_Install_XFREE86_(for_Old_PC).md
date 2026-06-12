---
title: "Desesperated: How Install XFREE86 (for Old PC)"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by patrick295767 on 2005-09-11
HI Linux Folks, 

I am just a novice with Debian and I am getting troubles cos I wanna 
install Xfree86 (the minimum X) for my very old PC ...

I installed UBUNTU from the CD as SERVER

So, now, it should be possible to install the Xfree86 or ICEWN ... 
but the easiest / faster for my old PC

my troubles are : HOW TO DO SO ...

I tried all things from net 
but mainly i got         
apt-get install x-window
apt-get install x-window-core

that  these stuffs x-window are not there ... 


Plz is there a prince who will be  telling me how to do line per line from console 
what i have to enter to have startx installed 

After doing apt-get install xserver-xfree86
it does find 
STARTX anywhere 


help help help 
It can be worth for users who want to install UBUNTU for OLD PC !!!!!!!!!!!

Thank you soo much

I hope that someone will reply me ...


Patrick

---

### Post by patrick295767 on 2005-09-11
after 

apt-get install x-window-system

it gives me 
the following packages have unmet dependencies

...

---

### Post by patrick295767 on 2005-09-11
i am progressing ...

I just enter in the console: 
(cos of my unmet dependencies)


apt-get -f install



and sthg happen ... you say YES 

then it's downloading ... 

... 

I hope it' ll be working ... 

still downloading ... 

we'll see ...

---

### Post by patrick295767 on 2005-09-11
Sooo that's great : now : 

Startx 
has been downloaded by the net 
and is somewhere in my PC 

that ''s really cool the downloading from the net !!!!

whaooo !

so let's progress and have a look now the startx 
results !!!

---

### Post by patrick295767 on 2005-09-11
ok so 

now , i have x screen 
with nothign ... only Xterm 

so my question is : 

how to have a normal windows manager like Icewn or gnome ... 
but easy .fast for my old pc !!!

let's work at it !!!

if someone is reading me,/helping me, i'll be pleased !!!

---

### Post by patrick295767 on 2005-09-11
now,  let's try 

apt-get install mozilla-firefox 

coool !!!!
it's downloading ... 
the internet web browser !!!

---

### Post by Leif on 2005-09-11
sudo apt-get install xfce4

or

sudo apt-get install fluxbox

---

### Post by patrick295767 on 2005-09-11
enter:

 wget [http://ahacic.5gigs.com/miniram.sh](http://ahacic.5gigs.com/miniram.sh)






[http://ubuntuforums.org/printthread.php?t=42873](http://ubuntuforums.org/printthread.php?t=42873)

---

### Post by patrick295767 on 2005-09-11
" 	sudo apt-get install xfce4

or

sudo apt-get install fluxbox"

thank you very much !!!!







soo,  i'll try the first one : xfce4


i  hope it's very better for old PC

.. i have to go for a dinner tonight restaurant ...  !!

So it'll be for later the workign progress... 


tbw,  enter:
wget [http://ahacic.5gigs.com/miniram.sh](http://ahacic.5gigs.com/miniram.sh)
was damn inportant to be done !!!

---

### Post by patrick295767 on 2005-09-11
xcfe4 is downloading lot lot lot

... i wanted the same like in drinou !!!

shit i guess i 'll have to start again from the begining ... 
i hope it wont be tooo much for my very old pc 

Drinou was working perfect : that s my target

thx ... 

dinner dinner.... i am gonna be late ... 

see ya '  :


Btw, LINUX is Great !!!

I am installing via the console rlogin  ...

---

### Post by patrick295767 on 2005-09-11
btw, 


looks not tooo slow

(someone know apt-get install ?????????????? to have the same as drinou (instead of xcfe4???)







----------------------------------

next target : 

1/ installing a FOLDER shared on this PC to the network with a login/passw

2/ hybernate tooo !!!!! as in windows 

3/ and managing to install Msn messenger 






------------

i installed xfmedia tooo !!!








see ya '' 


tahnx a lot Linux and very nice persons helping, ready for helping !!!

Good evening

remark : dillo is damn fast !!!!


----------

what is the xcfe4 instead in the world of drinou  / pitux ... it looks faster , no ??

thx a lot


good evening

---

### Post by patrick295767 on 2005-09-11
not working 


xcfe4 is tooooooooo much for the pc 

it should be the same as drinou ... 

i dont know to uninstall xfce4 now ... 
to put same as putix or drinou

thxn a lot 


pat'

---

### Post by Leif on 2005-09-11
try fluxbox then. it doesn't get any more lightweight than that. to remove xfce, 

sudo apt-get remove xfce4

---

### Post by spm on 2005-09-12
Did you fing you the recipe?

I'm trying to do something similar. I want a server with some X capability, very slim.


I installed Ubuntu as SERVER, installed Fluxbox...So far so good.

How do I get the xserver to start automatically? I want to login remotely, using something like

ssh -X -l mysuser

isssue xclock and have it popup.

Thanks for any help...Maybe we need a thread for superslim ubuntu with X.

I found Dillo (web browser) fast and small! Anything else?

---

### Post by patrick295767 on 2005-09-12
Hi, 

Nice restaurant yesterday !!!

--
okay ; i am gonna try the fluxbox too 
but i guess that twm is the faster and easiest maybe for very old prehistoric pc's...
I ll try too the icewm

i also have to try the xdm or wdm (i dont know the difference really yet)

(sthg important before 
# wget [http://ahacic.5gigs.com/sources.list](http://ahacic.5gigs.com/sources.list)
# cp /etc/apt/sources.list /etc/apt/sources.list_backup 
# cp sources.list /etc/apt/sources.list
# apt-get update
# apt-get upgrade)

(i made a ghost for trials...)

x starting automatically ... 
i dont know ... YET !!!!
it's somewhere with the ttys ...
I ll look in few days cos i have lot of work to do this week
if you find before me, let me know !!


"http://lists.freebsd.org/pipermail/freebsd-questions/2003-April/002251.html
try change your /etc/ttys file.

set tty8 (or 9, I am not using FreeBSD right now) from off to on, and
change the xdm to kdm (do not forget change the path) if you are using
KDE.

--Ken"



I am installing now the Icewm 
with xdm ...
... (and eating again)

I ll let u know about progress... 



--
My clue :
twm looks very very very very very very very very very very very very very very very very very very very very very simple 

i had that when i was installing my slackware 3.1 !!!!!!

see ya'

---

### Post by patrick295767 on 2005-09-12
I had that ' x automatically ' at my ing. school '  when student
so, if they managed to do that these admin guys...


It  means that it very very simple to be done !!!


--

---

### Post by patrick295767 on 2005-09-12
i tried twm and icewm

it s rather okay  icewm
but a bit too much for my old pc


twm is tried : 
result : it's prehistoric !!!!!!
no way !!


and fluxbox; it try to install it... 
but still cannot ... 
apt-get install fluxbox .. .
but i always get a twm instead ... 

progress progress

---

### Post by patrick295767 on 2005-09-12
result progress:

soo now, i have an operational operating system !!!


I installed x-system-core and so on 

then xterm, openssh-server, abiword, dillo, mozilla-firefox, and xpdf and a bit more


----------
then u install :
apt-get install fluxbox
apt-get install mc
apt-get install lynx

and to reply to ur question :
apt-get install xdm

the xdm starts automatically a x session 
where u can enter Login /passwd !!!!!!!!!!

that's the reply maybe ?? is it what u want ?


---------------------
concerning the fluxbox, 

U have to create :
.Xsession

and enter in it (with mc ):
fluxbox

---------------

that's it !!!

I have my linux adapted for my prehistoric PC !!!!!

actually, even fluxbox is rather asking tooo much 
but i cnanot use twm 
it's tooo shiity of having to click once u had  a window , e.g. xcalc xterm... 

is there a way to change the MENU in TWM ?????



FOR EXPERTs-(up) the question ...


Time to sleep ... 

Shit, linux is eating my nights !!

---

### Post by az on 2005-09-12
Fluxbox is broken in Hoary.  Use icewm.  Install the menu package

sudo apt-get install icewm menu

---

### Post by patrick295767 on 2005-09-13
Thx thx ... 


I made trials ... 
Even Fluxbox is rather to complex for my old pc ...

what i did was to remove the xdm in the installation
apt-get remove xdm 
and it  looks a bit lighter ... 

Also, instead of using Mozilla : OPERA is beetter and faster !!!

Also, I removed 2screens in Fluxbox ... 

It s working faster !!!

On damn small linux, I decreased the colors ....from 32K to ... (forgot)
and it was workign rather very fast ...
I guess that the colors are taking lot to CPU...
I dont know It looks ... 

It's still faster than windows 
but I am sure there is a way with linux to achieve very fast pc 's

is there sthg between the TWM  and Fluxbox
in terms of rapidity ?

ICEWM, i can retry again but I didtn got sufficient results .

Also, I got prob : once i installed OPERA 
it wasnt displayed in the menu of the Fluxbox
(i had to start it via XTERM ... )

Thx for reading, if you have courage !!

--
I go to bed ... 

Long life to Linux !!

nota: I cannot change location of my post now I guess 
(sorry (jestem newbie))

---

### Post by patrick295767 on 2005-09-13
I ll try on friday ur trick :

sudo su
apt-get install icewm menu

...
I dont really understand what it'll be doing ... 


and let you know ... 

see ya'

===================
IN TWM : I also wish to once u click on menu, u dont have to say 
where u wanna have ur window

and 2/ 
to have nicer menu 
(i guess u replied with apt-get install icewm menu)

...

---

### Post by patrick295767 on 2005-09-30
Results of the investigation : 

---
twm for slowest pc 
icewm and fluxbox are for faster pc (type 600Mhz)
---

Install yoru pc as UBUNTU server, then 

enter this:
$ sudo su -

# wget [http://ahacic.5gigs.com/sources.list](http://ahacic.5gigs.com/sources.list)
# cp /etc/apt/sources.list /etc/apt/sources.list_backup 
# cp sources.list /etc/apt/sources.list
# apt-get update
# apt-get upgrade

# apt-get -f install x-window-system-core

# apt-get -f install xdm (if you need a screen desktop rather automatically loaded when u start pc : wiht login / password) 

# apt-get -f install xterm

# apt-get -f install openssh-server


and so on !!!

.... 

Pat'

---

### Post by patrick295767 on 2005-09-30
------------------------------
to change screen resolution : 
sudo dpkg-reconfigure xserver-xorg
enter  yes ... and choose ur resolution u want 


--------------------
to install  a ftp server :
apt-get -f install proftpd
and
Start the Pro ftp daemon by running /etc/init.d/proftpd start


-------------

---

### Post by Leif on 2005-09-30
[QUOTE=patrick295767]
# wget [http://ahacic.5gigs.com/sources.list](http://ahacic.5gigs.com/sources.list)
[/QUOTE]

this source list is incorrect. the unofficial backports repositories have been shut down

---

### Post by patrick295767 on 2005-09-30
Thank you very much helping Newbies !!!! In total simplicity !

---

### Post by patrick295767 on 2005-09-30
then for additional programs to install , and huge amount of information: 

[http://ubuntuguide.org/#refreshgnomepanel](http://ubuntuguide.org/#refreshgnomepanel)

---------------------------------------------


apt-get -f install gnomebaker 
for a rather simple cd burner (x)

---

### Post by patrick295767 on 2005-09-30
I am using fluxbox for desktop 
it's rather fast and i am happy 

(that's personal information for Alexander)

(this thread is kind of How to ...)
(progressing in Linux and SHARING my work and results )


____________
LINUX

---

### Post by patrick295767 on 2005-09-30
for Internet : 

# apt-get -f install mozilla-firefox 



and for my old pc : 
# apt-get -f install dillo

---

### Post by patrick295767 on 2005-10-01
since the prob of mini ram how to ... the sources.list is oooold :

then please use the follwoign for the file /etc/apt/sources.list
then u do : apt-update
apt-upgrade
(and u can install then : apt-get -f install gaim xpdf )



# Example sources.list for Ubuntu hoary

## All officially supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## The source pacakges
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse

## The source pacakges
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse


## Backports - package version from a newer release build to work on the current
## no guarantees on working - not enabled by default
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## The source packages
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
#deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

---

### Post by patrick295767 on 2005-10-01
kind of notepad (windows version): 

apt-get -f install nedit

---

### Post by patrick295767 on 2005-10-01
Now, let's try to play with the other computer :
---------- I wanna send the app of remote pc on my local pc


It's normally very very easy :
PC1 is local
PC2 is not local
-----------

On the PC1 (local) in xterm: xhost + IP_PC2 
(to know your ip address: ifconfig)

then in another xterm on the pc1 :
rlogin IP_PC2
export DISPLAY=IP_PC1:0.0
xclock &

and xclock should appear on the PC1's screen...
   
   
   
=================
for instance : xmms 
works and uses the directory of the PC2 !! coool !! , but sound is running on the PC2 computer 
   
   
kaffeine doesnt like it apparently and bugs ... (?)

---

### Post by patrick295767 on 2005-10-02
Now the sound !!
=============

Is it working ?


enter in xterm:
aplay -l
lspci |less
lsmod |less

for instance, try to play mp3 with xmms  (apt-get -f install xmms)

and if not : 
in xterm, type:  alsamixer
(otherwise install it)
and un-mute the master, pcm, ... (with keyboard : m key)
increase the sound with arrows and it should work (I hope) 
'cos ubuntu is very nice distrib !!!

---

### Post by patrick295767 on 2005-10-02
to lock your screeen of X:
(download xlock i386 at [www.debian.org](www.debian.org)       => packages)
theen:

dpkg -i xlock*.deb

---

### Post by Lord Illidan on 2005-10-02
I am curious... How old is your pc? What are it's specs?

Ubuntu ran quite well on my Celeron 333 MHZ with 192 mb of RAM...
I guess the extra RAM was what it needed, though..

---

### Post by patrick295767 on 2005-10-05
is there a possibility of installing adobe photoshop
> in UBUNTU?
> what other WINDOWS-BASED application can i install
> Send instant messages to your online friends 

Search google for winehq. (Can't recall it's domain, probably 
[http://www.winehq.com/](http://www.winehq.com/) )
They have a database of working applications with wine (which is a working 
windows enverimont emulator).
I used to install Photoshop 7 with my previous Gentoo install and it worked 
90%.
HTH,

---

### Post by patrick295767 on 2005-10-05
[QUOTE=Lord Illidan]I am curious... How old is your pc? What are it's specs?
Ubuntu ran quite well on my Celeron 333 MHZ with 192 mb of RAM...
I guess the extra RAM was what it needed, though..[/QUOTE]

I have a Compaq Presario 1685 (K6-2, 380 MHz)
Ram 64 Mo - Dd 4.3 Go - Cd - Modem - 12.1" 

and I wished to have a very fast PC with it !!

The challenge is almost done with the TWM and ubuntu !

It's pretty nice result compared to windows, but I still wish to improve it !
Maybe buying ram could help too.

If you have any informations to improve performance, please let me know.

Patrick

---

### Post by patrick295767 on 2005-10-07
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

 /etc/apt/sources.list (use sudo), 


then 

apt-get update

apt-get install sun-j2re1.5

---

### Post by patrick295767 on 2005-10-08
To install kadu (gadu gadu client)

Hoary Hedgehog
echo 'deb [http://www.kadu.net/download/binary/ubuntu/repo](http://www.kadu.net/download/binary/ubuntu/repo) hoary main' >> /etc/apt/sources.list


apt-get update
apt-get install kadu


(eventually apt-get install kadu-alsasound kadu-extinfo)

---

### Post by patrick295767 on 2005-10-08
[QUOTE=patrick295767]is there a possibility of installing adobe photoshop
> in UBUNTU?
> what other WINDOWS-BASED application can i install
> Send instant messages to your online friends 

Search google for winehq. (Can't recall it's domain, probably 
[http://www.winehq.com/](http://www.winehq.com/) )
They have a database of working applications with wine (which is a working 
windows enverimont emulator).
I used to install Photoshop 7 with my previous Gentoo install and it worked 
90%.
HTH,[/QUOTE]


crossover is a very nice program that works pretty nicely.
I can now use in linux the OFFICE 2000, photoshop, totalcommander
This is workign pretty fast (almost like under windows) 
U can install programs u want... 
Clonecd, doesnt work (device not found)

It's pretty nice tool !!

Thanks linux !

---

### Post by patrick295767 on 2005-10-08
you can download vmware to emulate ur hdd pc or virutal pc 
That's pretty nice (rather fast)
but wine and crossover programs are faster 'cos no emulation.

For vmware, 30days program for free can be download on the web site
For crossover program, you woudl have to buy the cd to install office2000.
Wine works then much much better with crossover !!
That's pretty nice program 'cos we are not in emulation !!
yeah

---

### Post by patrick295767 on 2005-10-08
my fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hda3	/mnt/hda3	ntfs	defaults,rw,user,umask=000	0	2
/dev/hda1	/mnt/hda1	msdos	defaults,rw,user,umask=000	0	0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5	/mnt/hda5	ntfs	defaults,rw,user,umask=000	0	2
/dev/hdc	/mnt/hdc	auto	user,noauto,ro,unhide	0	1

---

### Post by patrick295767 on 2005-10-08
My sources.list:

# Example sources.list for Ubuntu hoary

## All officially supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## The source pacakges
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java


## The source pacakges
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse


## Backports - package version from a newer release build to work on the current
## no guarantees on working - not enabled by default
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## The source packages
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
#deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

---

### Post by patrick295767 on 2005-10-08
to make working the sound for all users : 
chmod 666 /dev/dsp

---

### Post by patrick295767 on 2005-10-08
to install gaim (msn yahoo ... messenger)

Please download the gaim-1.5.0.x86.package

it was a automatic package : this means the following :
you 'd have to do 

chmod +x gaim-1.5.0.x86.package

and run the file from xterm :
./gaim-1.5.0.x86.package

then the last version will be installed !

(sept-oct 05)

---

### Post by patrick295767 on 2005-10-08
Would it be possible maybe (eventually) to move this thread to the beginner location of our great ubuntuforums.org.

Thank you v. much!

Pat'

---

### Post by patrick295767 on 2005-10-12
[QUOTE=patrick295767]to make working the sound for all users : 
chmod 666 /dev/dsp[/QUOTE]

to make it at both reboot and switch on of pc :

make a file /etc/init.d/name_of_script.sh
with the following content:
#!bash
chmod 666 /dev/dsp
chmod 666 /dev/dsp1

then : chmod +x /etc/init.d/name_of_script.sh
update-rc.d /etc/init.d/name_of_script.sh defaults


then it's enabling the sound for xmms & for regular users...
I havent found other way but it works

---

### Post by patrick295767 on 2005-10-13
[QUOTE=patrick295767]Now, let's try to play with the other computer :
---------- I wanna send the app of remote pc on my local pc


It's normally very very easy :
PC1 is local
PC2 is not local
-----------

On the PC1 (local) in xterm: xhost + IP_PC2 
(to know your ip address: ifconfig)

then in another xterm on the pc1 :
rlogin IP_PC2
export DISPLAY=IP_PC1:0.0
xclock &

and xclock should appear on the PC1's screen...
   
   --------------
(?)[/QUOTE]

When u do : 
"Edit the file /etc/gdm/gdm.conf. Find the line that says "DisallowTCP=true"  and change it to read "DisallowTCP=false".
  
This is helping a lot the remote X.

---

### Post by patrick295767 on 2005-10-18
Hi, 

my last new : 
I replaced twm by fvwm on my old pc :
( apt-get install fvwm )

Robert Nation created fvwm in 1993 for 33 MHZ 486 laptop PC with only 4 MB of RAM: 


"RN> There were two or three reasons for starting FVWM and RXVT. First, I had
RN> a need 33 MHZ 486 laptop PC with only 4 MB of RAM, and I thought linux and X11 were 
RN> way better than the windows versions of the day. X11 with TWM and xterm would run on 
RN> my PC, but just barely. Second, I had a need at work to analyze spectrograms which
RN> were about 4000 x 200 pixels when displayed at full resolution (analyzing acoustic 
RN> signatures for the DOD) - twm couldn't display 
RN> that, although some other window managers could (they used more memory though!). Finally,
RN> I thought it would be nice to learn a few GUI software skills.

RN> I think I did rxvt first. The source code fro xterm was pretty hard to understand,
RN> so I found xvt on the net somewhere. I cleaned it up a bit and improved its vt-100 
RN> compatibility in a few areas. Next, I tore apart twm to find out why it was so big, and
RN> generated a very simple, low memory, low-flexibility version of a window manager. I added
RN> the virtual desktop stuff and started using it at work too, since it could display my
RN> spectrograms very nicely. 

RN> After I put the these things on the net, it was fun and educational for a while, as
RN> the programs became more capable. But as my kids got a little older and needed more
RN> attention from me), and the maintenance function got to be mostly integrating patches 
RN> from various people (and the patches had little or no utility to me), the fun went
RN> away, and Chuck Hines stepped up to take over.
"


Fvwm is great !! 
(Highly customizable too)

---

### Post by patrick295767 on 2005-10-18
For videos and DivX, i am using now : 
mplayer !!
that's the fastest for old pc 

that can be runned toooo without GUI !!

Differences obtained between Windows and Linux are Amazing !!
Movies that I couldnt play in Windows are now rather ok under Linux.
(fvwm (tried)).

I Like LINUX !!

Pat'

---

### Post by ygarl on 2005-10-18
Might look at apt-getting synaptic... then it'll be easier to look through and see what packages you need (and can get) for XFCE and IceWM.
I prefer Windowmaker myself, but that's just me...

---

### Post by patrick295767 on 2005-10-18
For Java2re1.5
----------------


[QUOTE=patrick295767]deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

[/QUOTE]


add deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java
to your  /etc/apt/sources.list (use sudo), 


then 

apt-get update

apt-get install sun-j2re1.5

---

### Post by patrick295767 on 2005-10-18
Re: How to make visible the Long-Names For My Fat32? (6-8chars maxi only :-( ) -  1 Minute Ago
---------------------------

the reply : vfat and not MSDOS is the key !!


in the /etc/fstab :
  
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda6 none swap sw 0 0
/dev/hda3 /mnt/hda3 ntfs defaults,rw,user,umask=000 0 2
/dev/hda1 /mnt/hda1 [SIZE="6"]vfat[/SIZE] defaults,rw,user,umask=000 0 0
/dev/hda4 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /mnt/hda5 ntfs defaults,rw,user,umask=000 0 2
/dev/hdc /mnt/hdc auto user,noauto,ro,unhide 0 1
/dev/sda1 /mnt/sda1 [SIZE="5"]vfat[/SIZE] defaults,rw,user 0 1
  
  
 
So, now, I can read loong names !!

---

### Post by patrick295767 on 2005-10-24
[QUOTE=patrick295767]For Java2re1.5
----------------





add deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java
to your  /etc/apt/sources.list (use sudo), 


then 

apt-get update

apt-get install sun-j2re1.5[/QUOTE]


And then, u can install LIMEWIRE by:
Apt-get install limewire

---

### Post by patrick295767 on 2005-10-24
Understanding better /etc/fstab
(mounting)
  
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
(by guyomarj)

---

### Post by patrick295767 on 2005-10-24
--------------------
how to check a checksum for free and very easily in windows  to prepare you to install linux on your pc !!
--------------------

Once u download the checksum file, just rename it as .sfv
(place it in the same folder of ur ISO file of ur linux CD)

Then install total commander from ghisler site :
[http://www.ghisler.com/](http://www.ghisler.com/)
(like mc under linux)

Then, click in the menu of total commander, Verify CRC !

and wait and see the results !

----------------------------------
Concerning ISO burning, if you burnt it with nero under windows, it should normally be well burnt. If you burn an ISO, the boot of the ISO should be present in the file and it'll result in a bootable CD without any problem. 
(u can check the boot of the cd with Winiso for instance (long but u can))

For instance, results are similar with K3b for linux...

So, sthg is wrong either in the burning or in the boot of ur pc maybe (try F11 - f12 or check in the bios maybe), or hardware prob ... or ISO corrupted or ... lot of possibilities ... 

----------

---

### Post by patrick295767 on 2005-10-24
How to install a rpm file ?
------------------------
(First, # apt-get install alien)
then,
  
alien -i FILE.rpm
or 
alien -k File.rpm
    
dpkg -i FILE.deb
   
      
  Results are not always great, ... so it's not sure that it'll be working !
But you can try if no other solutions ... 
For instance, for the ghostview, it's better to do : 
apt-get install gnome-gv
   
(than trying to convert the rpm)
  
apt-get install file1 file2 file3
will give you the best results.

---------------------------

---

### Post by patrick295767 on 2005-10-24
How to change your root password (if you forgot it) ?
------------------------------------------------
U can boot ur pc with knoppix or liveCD, 
mounting ur partition, (mount ...) 
  
then go into the shadow file of the /etc/
and copying the encrypted password of an user (password known)
or resetting the password of root ...(i guess 0:0 should work, ...I have to check)

Then, u reboot normally ur pc, and once root !
type to redefine ur root password:
passwd 

Good luck, please let me know about ur results !!!
('cos I forgot a bit)

Patrick

---

### Post by patrick295767 on 2005-10-25
[QUOTE=patrick295767]I had that ' x automatically ' at my ing. school '  when student
so, if they managed to do that these admin guys...


It  means that it very very simple to be done !!!


--[/QUOTE]

  To have that : simply install gdm or xdm or wdm 

# apt-get install gdm          // that's the best for me 

or
# apt-get install xdm          
  
or 
# apt-get install wdm

---

### Post by patrick295767 on 2005-10-25
[QUOTE=patrick295767]To have that : simply install gdm or xdm or wdm 

# apt-get install gdm          // that's the best for me 

or
# apt-get install xdm          
  
or 
# apt-get install wdm[/QUOTE]

With that u will have to enter LOGIN / PASSWORD .
wihtout using startx -- :0 
from the console 
----------

---

### Post by patrick295767 on 2005-10-25
K3B : burning DVD only not working ?? why ? this errormsg - 2 Days Ago 

--------------------------------------------------------------------------------

Devices
-----------------------
LITE-ON LTR-48125W VS06 (/dev/scd0, ) at [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
TOSHIBA DVD-ROM SD-R6112 1332 (/dev/hdc, ) at /mnt/hdc [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version: 3.3.3
Kernel: 2.6.10-5-386

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
:-( Failed to change write speed: 2117->2700

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=1 

mkisofs
-----------------------
/usr/bin/mkisofs: Warning: -follow-links does not always work correctly; be careful.
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
/usr/bin/mkisofs: Connection reset by peer. cannot fwrite 2048*1

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3b0Ag3Zb.tmp -rational-rock -hide-list /tmp/kde-root/k3bp9wi4b.tmp -full-iso9660-filenames -follow-links -iso-level 2 -path-list /tmp/kde-root/k3bWi90pb.tmp -dvd-video /tmp/kde-root/k3bVideoDvd0 /root/.kde/share/apps/k3b/temp/dummydir0/ 




my fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda6 none swap sw 0 0
/dev/hda3 /mnt/hda3 ntfs defaults,rw,user,umask=000 0 2
/dev/hda1 /mnt/hda1 vfat defaults,rw,user,umask=000 0 0
/dev/hda4 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /mnt/hda5 ntfs defaults,rw,user,umask=000 0 2
/dev/hdc /mnt/hdc auto user,noauto,ro,unhide 0 1
/dev/sda1 /mnt/sda1 auto user,noauto,rw,unhide 0 1 
 
     
 --------------------------------------------------------------------------------

In the window just before starting burning, I tried "Ignore" speed 
instead of AUTO:
==> and it worked !!!!!!!!! I can now burn dvd.

The reason comes from the hardware... some people should have same experience with laptop  & the dvd burner...

---

### Post by patrick295767 on 2005-10-26
How to make your own script ??    
---------------------------------
Summary: 
1-Short Example
2-Link to the detailed page concerning scripts (interesting and still rather simple for beginning)
Additional informations concerning


(1) This little example, will check your internet connection state with a very universal and simple way each time u login your Linux Box :
  
  
so,  
You could add at the end of your .bashrc

type: vi .bashrc
then go to the last line 
press: several times i key (like insert)
enter the last time as below
press ESC key several times 
enter:
:wq 
//(double point, w and q) = write and quit
------------------------------------------------------------------------ 
.bashrc
--------
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

and so on .... 

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

./prog-ping2.sh
------------------------------------------------------------------------


then type:
gedit prog-ping2 &
   
------------------------------------------------------------------------
prog-ping2
------------
#!/bin/bash
mkdir ~/netstat
cd ~/netstat
variable01=$(date)-ADSL-result.txt
echo ${variable01}
echo "Performing a ping investigation..."
echo "$(uname) $(uname -r)" > "$variable01"
echo "$(date)" >> "$variable01"

ping -c 30 [www.google.com](www.google.com) >> "$variable01"
echo "** ADSL Ping Performed **" >> "$variable01"
echo "** ------$(uname)$(uname -r)------- **"
echo "********************"
variable02="$variable01 $(echo $(cat "$variable01" | grep "min/avg/max" | cut -c32-38 ))"
variable03=$(echo $(cat "$variable01" | grep "min/avg/max" | cut -c32-38 ))
echo "$variable02"
echo "***"
cp "$variable01" "$variable02" 
echo "** copied **"
cp "$variable01" "$variable01$(date)"
rm "$variable01"
echo "$variable01"***copied*to "$variable02"**"with"***"$variable03"
echo "****Process Done*****"
------------------------------------------------------------------------
   
   
  
Once done, type:
ls -l
chmod +x prog-ping2
ls -l
  
U see the prog-ping2, changed to green color: this means that u made a script file.
type: 
./prog-ping2 &
and look the result in the ~/netstat folder
   
  
  
(2) The link for scripts you could go is as follows:
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)
  
It's very nice website for beginning.
  
  
I hope these little example and information will help you for starting your own basg script !!
  
Best regards, 

Patrick

---

### Post by patrick295767 on 2005-10-27
How to share your folders with nfs  (server-linux box, client-linux box ... ) (no windows)
(if windows, please install the samba)
--------------------------------------------------------------------------------
  
(1) First:
# Apt-get install nfs nfs-common
(nfs-utils maybe)
  
(2)
----- SERVER PC 192.x.x.15--------
/etc/exports : 
----------------------
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).

/mnt/sda5	192.x.x.15(rw)	192.x.x.16(rw)
/mnt/sda9	192.x.x.15(rw)	192.x.x.16(rw)
   
  
  
-------SERVER PC --- 192.x.x.15 -----
/etc/hosts.deny :
--------------------------
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

portmap:ALL

    lockd:ALL
    mountd:ALL
    rquotad:ALL
    statd:ALL


-------SERVER PC --------
/etc/hosts.allow :
--------------------------
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and 
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#

portmap: 192.x.x.15 , 192.x.x.16
   


    lockd: 192.x.x.15 , 192.x.x.16
    rquotad: 192.x.x.15 , 192.x.x.16
    mountd: 192.x.x.15 , 192.x.x.16
    statd: 192.x.x.15 , 192.x.x.16

   
-----------------------------------------------------------
(3)then type: 
exportfs –ra
exportfs –ra
exportfs –ra
(to be sure … )
   
   
--------------------------------------------------
----- Client PC 192.x.x.16 --------
/etc/fstab:
----------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

and so on
and:

192.x.x.15:/mnt/sda5	/mnt/folder5	nfs	rw,hard,user	0	0
192.x.x.15:/mnt/sda9	/mnt/folder9	nfs	rw,hard,user	0	0

-----------------------------------------------------
    
    
----- Client PC 192.x.x.16 --------
(maybe chmod +s /… / smbmount
maybe chmod +s /… / smbmnt
can be done if some troubles with rights)
  
Users can mount their nfs with :
mount -t nfs 192.x.x.16:/mnt/sda5
   
If some additional information can be added...Please let me know by sending my a ubuntu-private-message, progress progress ... I would like to know more about it... 
  
I wish that will help a bit.

With my best regards,

Patrick

---

### Post by patrick295767 on 2005-11-05
How to start another GDM session in parallel on the :1 ??
-------------------------------------------------
(one gdm on the Xscreen :0)
and (another gdm on the X screen :1)
   
So, in the file :
/etc/X11/gdm/gdm.conf

please mention that u'll like it in both :0 and :1
That should be indicated as follows :
...
[servers]
# These are the standard servers. You can add as many you want here
# and they will always be started. Each line must start with a unique
# number and that will be the display number of that server. Usually just
# the 0 server is used.
0=Standard
1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken). Using 7 will work
# pretty much for all linux distributions. VTAllocation is not currently
# implemented on anything but linux and freebsd. Feel free to send patches.
# X servers will just not get any extra arguments then.
#
...

Regards,
   
  
----------- XDMCP -------------------------------------
then u can do:
sudo gdmsetup
select the last one (where u can choose the XDMCP very easily at the login/password for ur X session)
  
then, u could choose XDMCP
select the IP_server_PC/ or DNS_PC_Server (remote pc)
  
then, u'll get on ur pc the remote X session on the distant PC!
  
This is very very great for very old PC !!
You could use program that are using lot the CPU and impossible for old pc.
This would enable you to work on the distant server Pc with higher configuration for heavier programs.
  
(plz, have a look in the following post : How to setup ur XDMCP (on the server_PC) )

Regards, 

(If you'd like more info, plz dont hesitate to contact me)

Patrick

---

### Post by patrick295767 on 2005-11-05
How to setup XDMCP for server /client:
----------------------------------------------  
on SERVER XDMCP / SERVER of X session:
   
Modify in the    /etc/gdm/gdm.conf as:
```
        [xdmcp]
Enable=true   

```
   
restart the gdm :
```
# /etc/init.d/gdm restart

Stopping GNOME Display Manager: gdm.
Starting GNOME Display Manager: gdm.
```
   
That's all !!
----------------
  
Client using the X session from the Remote_PC_Distant:
thsi is very very useful for old pc !!, e.g. u can use XDMCP to access a computer with higher configuration and be using its powerful CPU ==> then, on ur old pc, u can run heavy programs via using the XDMCP !!
  
First method: from the console
-------------
go into the tty1 console
by pressing : ALT CTRL F1
then u can enter:
X :1 -query IP_address_Of_Remote_server
(:1 is the second X server (in case u are using (xdm/ wdm or) gdm ))
   
Second method: from the gdm :
(gdmsetup and select the last theme for gdm)
(then u can see in the middle of gdm login/password screen an icon ACTION)
In the action icon, once u click on it, u'll get the possible linux box wiht XDMCP enabled in the network
just click on it, and u'll get runned ur XDMCP distant session like magic
     
Additional information, if u run mplayer or xmms (via distant), the sound will be played by the server/distant  pc and not on the client :-(
  
  
  
   ---------------------
(very nice website: additional information: 
[http://people.via.ecp.fr/%7Ealexis/formation-linux/export-display.html](http://people.via.ecp.fr/%7Ealexis/formation-linux/export-display.html))
 
   
 
Greetz'
For more information, please dont hesitate to contact me !!

---

### Post by patrick295767 on 2005-11-05
my fvwm config file : (for the moment !! )
~/.fvwm/.fvwm2rc:
fast, efficacity & simple (beautiful enough)
--------------------------------------------------------
I like : 
alt mouse left click : move window
alt mouse right click : resize window
mouse middle click : iconify 
alt mouse middle click : raise/lower
  
[http://www.lynucs.org/index.php?screen_id=73223288443f89d668f776&p=screen](http://www.lynucs.org/index.php?screen_id=73223288443f89d668f776&p=screen) 

and my ~/.fvwm/.fvwm2rc:
[http://fvwm.lair.be/viewtopic.php?p=6595#6595](http://fvwm.lair.be/viewtopic.php?p=6595#6595)
   
  ================
 ==============
Version 02 & much more beautiful & much better... :
(& transparency ...:)
[http://fvwm.lair.be/viewtopic.php?t=1240&highlight=](http://fvwm.lair.be/viewtopic.php?t=1240&highlight=)
  
   
   
======================
   
fvwm & memory :
========
1.6  What's the relative memory usage for the various window managers
     out there?

A: Here's a little table comparing some of them.  It was done on an
   AIX based IBM RS6000 model 355 using the same number of windows (3)
   and XSession to switch between the window managers, and I used
   'top' to show the values:

      SIZE   RES
      545K  652K fvwm2 (fvwm 2.0.35)
      457K  528K fvwm  (fvwm 1.24rb)
      856K  960K ctwm  (ctwm 3.2p1)
     1004K 1156K mwm   (mwm 1.2)
      543K  632K twm   (???)
      263K  328K aixwm (a simple ugly window manager included w/ aix)

---

### Post by patrick295767 on 2005-11-07
[SIZE="4"][/SIZE][QUOTE=patrick295767]to make it at both reboot and switch on of pc :

make a file /etc/init.d/name_of_script.sh
with the following content:
#!/bin/bash
chmod 666 /dev/dsp
chmod 666 /dev/dsp1

then : chmod +x /etc/init.d/name_of_script.sh
update-rc.d /etc/init.d/name_of_script.sh defaults


then it's enabling the sound for xmms & for regular users...
I havent found other way but it works
**[SIZE="3"]This script will start at startup and shutdown of PC (-r & -halt) [/SIZE]**[/QUOTE]  
   
---Now...-----------------------------------------------------------------
How to make a script for the startup of the Linux Box :
------(**this one doesnt start when shutting down / rebooting pc, only for startup of Linux Pc  **) -------
    
cd /etc/init.d
vi patscript.sh
sudo chmod +x /etc/init.d/patscript.sh

sudo ln -s /etc/init.d/patscript.sh /etc/rc2.d/S15patscript.sh
(this only creates the start in runlevel 2 with priority 15)  
            
  
--------------------------------------------------------------------
Other stuffs (found):
Put them in /etc/init.d/. Then use

Code:
sudo rcconf
and check the box against the appropriate script to run it on every boot. Make sure the files are executable.
If you get a command not found on rcconf use

Code:
sudo apt-get install rcconf
--------------------------------------------------------------------

---

### Post by patrick295767 on 2005-11-07
How do I change screen resolution?
---------------------------
I usually use the : 
```
sudo dpkg-reconfigure xserver-xorg
```
  Then U'll get menu's to reply to:
  
u can enter/ select the defaults values if you really dont know... 
... 
set only one screen I want 
    
last step of the config. procedure:
,and, then u can select :
simple (screen size)
medium (choose ur resolution)
> expert (lot of to set up) <  
  
Pat'

---

### Post by patrick295767 on 2005-11-08
In the progression thread, a quote from Kyral (Ubuntu Baristas), an wicked & amazing explanation of the X Window Managers:
  
For my case of Old PC, I personally chosed the FVWM as previously gave my config file .fvwm2rc. (one desk / pager    1*1, to save memory) 
with rox-filer (from [www.debian.org](www.debian.org))  ([http://rox.sourceforge.net/phpwiki/static.html)](http://rox.sourceforge.net/phpwiki/static.html)).
   
  
>   Window Managers for Beginners - 

--------------------------------------------------------------------------------

Just like how my Terminal For Beginners came into being, I have heard the same general question. "What is a Window Manager and how do they work" (or basically that)

Well, here I am again to explain another fundemental part of the Linux system, in my usual flair 

Now before we can understand Window Managers, we have to understand what makes the GUI system in Unix-based systems(Linux, OSX, the BSDs, etc) from the GUI system in XP. Now you know that in XP, if GUI crashes, it takes the entire system with it. Because for the most part, the GUI is the system (Feel free to correct me, I don't know a lot about the inner workings of XP). However in Unix-based systems, the GUI is separate from the system, in the form of X.

Now what is X? Well, its technically called "The X Windows System". It is also referred to as the X Server, which is also right, but for techinical reasons that aren't need to be understood now. Most of the time its referred to as X. What makes X different is that it frankly doesn't CARE what runs on it. It just handles drawing the screen, plus mouse and keyboard input. This allows for the almost infinite various GUI designs you see on Linux systems.

Now if X doesn't care what the GUI looks like, what does? Well, now we are at Window Managers. Window Managers are what control the placement and look of the application windows. Most also provide the menus we interact with and the cool panels and docks that we love so much. There are many Window Managers out there. What follows is a list of the most common and popular

Wait a SECOND! I can't do it yet! I have to explain one other concept. The Desktop Environment. There are only 3 Desktop Enviroments in the Linux world. XFCE, GNOME, and KDE. What makes a Desktop Environment different than a Window Manager? Basically, the amount of stuff that it provides. Desktop Environments typically have thier own File Managers, default Web Browsers, graphical Control Panels, and applets. However, they also need a Window Manager to run on top of. Now KDE has one integrated in, as does XFCE. But GNOME doesn't, and depends on one of the Window Managers listed below to help it out. Okay? Cool! Lets go!

TWM (Tab Window Manager or Tom's Window Manager): The very basic and default WM that X ships with. In its default state its not much more than a way to have multiple terminals on the screen. However rumor has it that its very customizable if you know C and about the XLibs...

BlackBox - This WM is one of the "Box" series of Window Managers. Very minimalistic, yet also very FAST. Just a step above TWM in its default configuration, it is nonetheless a favorite with power users.

FluxBox - Fluxbox is decended from Blackbox, and as such inherits a lot of its traits. Aims to be VERY simple, yet also has a bunch more things that Blackbox lacks. Most of its configuration is done with text files. In its default configuration it only provides a taskbar and a main menu which is accessed via right click. However I have seen INCREDIBLE looking desktops come out of Fluxbox.

FVWM: (F Virtual Window Manager) - Directly decended from TWM, FVWM nonetheless is still kicking, and many other Window Managers are decended from it. Almost endlessly customizable, its still a favorite. (Wikipedia Entry with MUCH more info)

Enlightenment - The very powerful WM, distantly decended from FVWM, Enlightenment is one of the favorite Window Managers today, going toe to toe with Desktop Environments like XFCE, GNOME, and KDE. Known for its unique take on the Virtual Desktop concept, Enlightenment is the Window Manager that is closest to being a Desktop Enviroment. This is even more true with the pending release of Enlightenment DR17, or just "E17", which promises to knock out everyone with how much eyecandy it can produce with so little resources. It should be noted that Enlightenment can be combined with GNOME to produce what is referred to as "Enlightened GNOME".

MetaCity - This Window Manager is only notable for being the default Window Manager in GNOME.

OpenBox - Another WM based on Blackbox, its quick, light, and fast. Its often used to replace MetaCity in GNOME. 

Desktop Environments

Mezzo - This still in development Desktop Enviroment is the star attraction for SymphonyOS and looks very promising. It completely discards the traditional GUI design concepts that GNOME, KDE, and XFCE seem to follow in favor of making the desktop more usable. Its really something that has to be used to believe. Distantly based off of FVWM. In case you can't tell, I think this project is going places 

XFCE - XFCE, the 3rd Desktop Environment that is almost always in the shadow of GNOME and KDE, is the default desktop environment for Xubuntu. Very streamlined, it is the DE of choice on slightly older systems. However it also boasts some very cool powertoys, namely the best compositing manager out of the three Desktop Environments (compositing is what lets things like drop shadows and "true" transparency happen). Many themes are available, and even shares many themes with GNOME due to thier common language of GTK. I personally run this DE. Themes 

GNOME (pronouced "Guh-nome") - One of the Big Two Desktop Environments alongside KDE, GNOME is the default Desktop Environment of Ubuntu and also of the GNU Project. Created in 1997 out of concern that KDE's use of the Qt libraries would take it out of the realm of free software, GNOME uses the GIMP Toolkit, better known as GTK. It comes equipped with Epiphany as its web browser, Evolution for mail, GAIM for IM, The GIMP for Image Work, Abiword for Word Processing, Totem for videos, Nautilus for file browsing, and Rhythmbox for music playing. Unique out of the Desktop Environments in that it doesn't have its own Window Manager. Currenlty uses MetaCity, in the past has used Enlightenment and Sawfish as defaults. Notice that Ubuntu's GNOME doesn't come with the apps I listed as default. Those apps are actually apps that are designed to fit in with GNOME. Themes and more

KDE (K Desktop Environment) - The original Linux Desktop Environment and the default for Kubuntu users, KDE is the main "rival" for GNOME. It was created in 1996 and ran into some controversy with the Free Software folks over its use of the then proprietary Qt Libraries as its method of drawing graphics. More "eye-candy" that GNOME or XFCE, KDE has been accused of trying to emulate Windows XP in style and look. However many VERY cool apps have come from KDE, namely Amorok, k3b, and Krita. Currently uses Konqeror(sp?) for web/file management, Kontact for email, Kopete for IM, and Adept as a replacement to Synaptic. It also has a good Compositing manager. Themes and more

Oh, one final note. There is no such thing as a "GNOME App" or a "KDE App". It doesn't matter what WM/DE you are using, they will work the same. Granted it may look a little out of place, but it will still work perfectly. Heck I run XFCE and I use k3b on a regular basis. 

So I hope I have once again provided information on another part of the Linux Mythos.


--------------------------------------------------------------------------------

Registered Linux User #390528
Terminal For Beginners
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)
[https://wiki.ubuntu.com/NewUserMentors](https://wiki.ubuntu.com/NewUserMentors) 

----------------
screenshots: 
[http://xwinman.org/](http://xwinman.org/)
   
------------
to install the fluxbox, ... 
the 'apt-get install fluxbox '  won't work  (broken package)
please downlaod it from the [http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)
to install it.
-----------------

---

### Post by patrick295767 on 2005-11-08
For Old, Internet speed browser:
-----------------------------------
Opera appears to give best resutls for old pc
PC [http://www.howtocreate.co.uk/browserSpeed.html](http://www.howtocreate.co.uk/browserSpeed.html)
   
In case, that Opera is still tooo slow:
heavier: dillo
            lynx2
            lynx (no images)
  
Regards,

Pat'

---

### Post by patrick295767 on 2005-11-08
How to avoid the grub error 21 with vmware:
----------------------------------------------------------
Vmware for linux is a very nice program for emulating the windows OS.
[http://www.vmware.com/support/guestnotes/doc/](http://www.vmware.com/support/guestnotes/doc/)
   
U can with this progr start Windows Onto LINUX !!!  (fullscreen or as mini wiindow in linux)
  
If you encounter the "grub error message 21" while trying to use the partition of ur harddisk 
  
harddisk :
partition01: swap linux
partition02: linux
partition03: Windows
   
the reason certainly would come from ur config of vmware.
  
In order to use ur partitionO3, u should mention : CUSTOM
and select to use FULL HARDDISK and Not Only The Single Partition Partition03 !!!
  
Then, once u start the program Vmware, u select from the Grub (dual boot (if)) the Windows OS ... 
and that's it !! 
  Windows into Linux.
  
Vmware is pretty fast. 
Please also dont forget to install the vmware tools to avoid any problems.
While doing so, u'll see in ur explorer of windows, u'll have a folder with programs that will enable u to install the video driver (that's not the same of linux) ... u'll see 
  
  
Pat'

---

### Post by patrick295767 on 2005-11-16
Hi guys, 
  
So, in order to install LINUX for old pc... I found the way : installing the ubuntu linux as server and then to add programs manually one per one (a bit as a miniram.sh)
  
I made this:
Please check a bit the script before...
and download the sources.list  and copy them in the /root/ (and copy them there: /etc/apt/sources.list)
 
  (script to be run as root)
```
#!/bin/bash
echo " Processing ..."
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
  
apt-get update
apt-get -y upgrade
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xfree86 xdm 
apt-get -f -y install openssh-server
apt-get -f -y install samba
apt-get -f -y install proftpd
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip
apt-get -f -y install 
apt-get -f install
apt-get install
apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install nfs nfs-common
apt-get -f -y install

echo " the startup of Linux $(uname -r) "
echo "#!/bin/bash bash for startup linux" > /etc/init.d/patrickrcs70.sh
chmod +x /etc/init.d/patrickrcs70.sh
cd /etc/init.d/
ln -s patrickrcs70.sh /etc/rc2.d/S70patrickrcs70.sh
echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5
dpkg-reconfigure xserver-xorg
echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
##echo "fvwm" > "/home/$1/.Xsession"
##echo "/home/$1/.Xsession"
##echo "set up the fvwm as default"
apt-get -f -y install 
echo "Please choose gdm "
apt-get -y install gdm
apt-get -y install x-window-system-core
apt-get install
apt-get install
apt-get clean
/etc/init.d/gdm restart
echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"



```
   
Nota: After server installation: Size used = about 330MB
and after my installation script : size used = about ~1500MB
  (nota2: I put xfree86 but at the end it works fine with xorg )
(if you know to improve the script, please let me know) 
  

  
Greetz',

Patrick

---

### Post by patrick295767 on 2005-11-21
g

---

### Post by patrick295767 on 2005-11-21
g

---

### Post by patrick295767 on 2005-11-23
Linux Boot Scripts
Richard Gooch

21-NOV-2002

[http://www.atnf.csiro.au/people/rgooch/linux/boot-scripts/](http://www.atnf.csiro.au/people/rgooch/linux/boot-scripts/)

---

### Post by patrick295767 on 2005-11-24
Very useful Softwares & Programs for Linux  (home and work application):
----------------------------------------------
Architect: [http://www.archilinux.org/autocad/acad.html](http://www.archilinux.org/autocad/acad.html)   (autocad type)
Pictures Prog... 
List of programs: [http://www.archilinux.org/archi-linux/archilinux.html](http://www.archilinux.org/archi-linux/archilinux.html)
(screenshoot + Link)

---

### Post by patrick295767 on 2005-12-16
Network functions :
------------------
Like traceroute, ifconfig, rdate ...

[http://rak.isternet.sk/linux-netman/commands.html]("http://rak.isternet.sk/linux-netman/commands.html")

---

### Post by patrick295767 on 2005-12-16
My script to install a server ubuntu:
-------------------------------------

Have a look to make a bit ur own modifications... 

```
#!/bin/bash
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
##cp "/root/.fvwm2rc" "/home/$1/.fvwm/.fvwm2rc"
apt-get update
apt-get -y upgrade
apt-get -f -y install x-window-system-core
apt-get -f -y install xdm 
apt-get -f -y install openssh-server
apt-get -f -y install samba
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install proftpd
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install gnome-chess
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install xpdf 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip

apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install nfs
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install xzgv
apt-get -f -y install nfs nfs-common
apt-get -f -y install 
apt-get -f -y install 

echo " the startup of Linux $(uname -r) "
echo "#!/bin/bash" > "/etc/init.d/bootcs70.sh"
echo "chmod 666 /dev/dsp" >> "/etc/init.d/bootcs70.sh"
chmod +x /etc/init.d/bootcs70.sh

cd /etc/init.d/
ln -s bootcs70.sh /etc/rc2.d/S70bootcs70.sh
echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5

echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
echo "** crossover is nice prg for windows apps**"
echo "fvwm" > "/home/$1/.Xsession"
echo "/home/$1/.Xsession"
echo "set up the fvwm as default"
apt-get -f -y install 
echo "Please choose gdm "
apt-get -f -y install 
apt-get -y install gdm
apt-get -y install x-window-system-core
apt-get -f -y install xserver-xorg

apt-get -f -y install 
dpkg-reconfigure xserver-xorg
apt-get -f -y install 
apt-get clean
/etc/init.d/gdm restart
echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"




 
```

---

### Post by patrick295767 on 2005-12-16
How to mount ur windows xp partition
=========================
to know which one : qtparted or fdisk /dev/hda
  
  
First make a folder for windows to be mounted in.


```
sudo mkdir /media/windows
```


Then mount it. If you are running windows XP on /dev/hda1, (the first partition in the drive) use:

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```


Adjust accordingly for Fat32 etc.

---

### Post by patrick295767 on 2005-12-17
My X desktop choice : 
============

My favourite is always the fastest & lightest, with simplicity & efficiency !!
I choosed fvwm but this requires more experience & a bit of time concerning customization !
So, I am using fvwm with gnome apps and also a bit of kde prg.
mainly : "fvwm desktop with a gnome-panel on the top", with a screen scrolling (a bit like strategy games, e.g. age of empire and so on...), efficient thumbnails ...
autohiding windows ...

Have a look there to give u an idea, and let me know what u think about this :
[http://dev.gentoo.org/~taviso/screenshots/tour.avi](http://dev.gentoo.org/~taviso/screenshots/tour.avi)
(this is a very nice video from taviso !! thanks again !)

Kind regards,

Patrick

---

### Post by patrick295767 on 2006-01-07
Mixing kde, gnome, .... for your Linux comfort 
==========================
  
  
Code:

```
apt-get -f install kdm
``` is for installing the X login / password, made by kde (screen :0.0)
```

apt-get -f install gdm 
```is for installing the X login / password, made by gdm (I prefer this one cos u can setup up more things)

If you dont install gdm ,kdm or xdm, you may login a X session via the console and type:
```
startx -- :0.0
```
or
startx -- :1.0
depending on the screen you wanna choose.
(alt ctrl F7 ... F12, to switch between them)

```
apt-get -f install kde
``` is for installing the kde desktop

```
apt-get -f install gnome 
```is for installing the gnome desktop

Concerning ur session of fvwm, xfce, ... gnome, kde, you may select in the gdm or kdm (btw xdm exist too) , the X desktop u wanna use, eg fvwm.
U can use fvwm with apps of kde or gnome or xfce ...
You are totally free of having for instance a
fvwm with a kicker bar or gnome-panel bar with kde or gnome apps, with a scrolling of your pagers into ur desktop, like strategy games (age of empire ...)

Linux is cool,isnt it !

Greetings,

---

### Post by patrick295767 on 2006-02-21
--------------------------
Is it Possible to copy with dd the Grub in the MBR ? (Before-installing-Windows)
-----------------------------------
   
```
sudo dd if=/dev/hda of=/root/MBR_image.img bs=446 count=1
```
( first sector (512 bytes)  - 2 byte number - 64 byte partition table)

---

### Post by patrick295767 on 2006-02-21
Installing Amsn 0.95 
---------------------

Download this:
[http://prdownloads.sourceforge.net/a...5-3.ubuntu.deb](http://prdownloads.sourceforge.net/a...5-3.ubuntu.deb)

And :

```
sudo apt-get -f -y install amsn
```
```
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```

---

### Post by patrick295767 on 2006-02-21
Changing the gdm login manager config:
-------------------------------------
   
```
sudo gdmsetup
```
if you installed gdm (login manager)...
I prefer thsi one much better than kdm, 'cos with
gedit /etc/gdm/gdm.conf
u can customize a lot of things

U wanna change it :
Go to [http://art.gnome.org/themes/gdm_greeter/](http://art.gnome.org/themes/gdm_greeter/)
or  [www.gnome-look.org/](www.gnome-look.org/)
and download the file
(do not unpack it)
and with gdmsetup, u may select the one u like

---

### Post by patrick295767 on 2006-02-21
---------------------------
How do I make a disk image    
For instance, whole disk (/dev/hda)       or   partition (/dev/hda1)
----------------------------
first, get information about ur disk : 
```
fdisk /dev/hda -l 
```
or 
```
cfdisk /dev/hda
```

U can use dd from the knoppix bootable cd
([http://www.knoppix.org/](http://www.knoppix.org/))
u can then mount from the network to ur present installed pc via nfs:

After sharing one folder on ur "server" pc .... (bla bla) (/mnt/sharedfolder for instance)
(exports allow autofs ... )

```
dd if=/dev/hda bs=1k conv=sync,noerror | gzip -9 > /mnt/sharedfolder/image-backup.img.gz
```

On the new pc, booted with knoppix cd:

```
mkdir /mnt/server
mount -t nfs IPaddress_of_server:/mnt/sharedfolder /mnt/server
gzip -dc /mnt/server/image-backup.img.gz | dd of=/dev/hda
```

(that's a quick example)

Enjoy Linux !

---

### Post by patrick295767 on 2006-02-22
**----------------------------------------------------------**
**Updated list of Working Webcam under Breezy: Plug&See :**
**---------------------------------------------------------**
**(no compiling) Easily working:**


logitec spacecam150
Logitech Quickcam pro 400 Drivers can be downloaded from ubuntu repositories.

[Nice web site ab webcams ]("http://mxhaard.free.fr/download.html")

Webcam qui marche avec amsn/ubuntu :
- creative webcam3
- philips TOUcam pro
- Logitech pro 4000 (uniquement en réception image)
- Quickam express Logitech (tuto ici, mais ca ne veut pas dire qu'elle roule avec amsn...)
- Webcam logitech clcik smart 510
- Logitech Quickcam Communicate
- Logitech Sphère
- Toshiba Portégé R100
- Labtec Webcam Pro
- Webcam LDLC
- Nikon Coolpix 4100

Webcam qui marche pas avec amsn/ubuntu :
- Labtec DC-2320



[B]--------------------------------------
For the following webcams: u may download [there ]("http://blognux.free.fr/sources/debian-cam/usr/share/")the following files and compile ... [/B]
**Compiling there is required ... **

ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
ID 05a9:8519 OmniVision Technologies, Inc.
ID 05a9:4519 OmniVision Technologies, Inc.
#Identifiant OK
ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
ID 0471:030c Philips PCVC690K WebCam
ID 0471:0310 Philips PCVC730K WebCam
ID 046d:0850 Logitech, Inc. QuickCam Web
ID 046d:08f0 Logitech, Inc
ID 046d:08f0 Logitech, Inc.
ID 046d:0870 Logitech, Inc. QuickCam Express
ID 046d:08f5 Logitech, Inc.
#ID ok

ID 046d:0920 Logitech, Inc. QuickCam Express
ID 0ac8:301b Z-Star Microelectronics Corp. Sansun SN-510 WebCam
ID 04fc:0561 Sunplus Technology Co., Ltd
ID 041e:4028 Creative Technology, Ltd
ID 046d:0901 Logitech, Inc. ClickSmart 510 
ID 046d:0960 Logitech, Inc. ClickSmart 420
ID 041e:4036 Creative Technology, Ltd Webcam Live
ID 041e:401e Creative Technology, Ltd WebCam NX Pro
ID 046d:0900 Logitech, Inc. ClickSmart 310
ID 0c45:60c0 Microdia
ID 041e:401d Creative Technology, Ltd WebCam NX Ultra
ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
ID 0c45:602d Microdia
ID 046d:08a2 Logitech, Inc.
ID 041e:401f Creative Technology, Ltd Webcam Notebook
ID 093a:2468 Pixart Imaging, Inc.
ID 046d:08ad Logitech, Inc.
ID 093a:2468 Pixart Imaging, Inc. CIF Single Chip
ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
ID 054c:0154 Sony Corp.
ID 054c:0155 Sony Corp.
   
  
Logitech quickcam express works with this script:
from arnie :
> #!/bin/bash
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz)
tar xvfz spca5xx-20060202.tar.gz
cd spca5xx-20060202
make CC=gcc-3.4
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx
 
Associated Post with nfo ... for thsi webcam : [http://www.ubuntuforums.org/showthread.php?t=133777](http://www.ubuntuforums.org/showthread.php?t=133777)
Once done, I checked with camorama 
No frozen linux, & I got my first Picture !
 ============

Nouvel Edit :
Voici des liens utiles trouvés :
- le wiki ubuntu pour installer une logitech [http://wiki.ubuntu-fr.org/materiel/webcam_logitech_msn](http://wiki.ubuntu-fr.org/materiel/webcam_logitech_msn) [http://mxhaard.free.fr/](http://mxhaard.free.fr/)
- Pilote Linux de webcams SPCA5xx [http://www.trustonme.net/didactels/172.html](http://www.trustonme.net/didactels/172.html)
- Installation des pilotes pour les webcam Logitech, LegoCam, Dexxa et Labtec [http://www.trustonme.net/didactels/172.html](http://www.trustonme.net/didactels/172.html)
- Quickcam Messenger & Communicate driver for Linux [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)
- CPiA webcam driver for Linux [http://webcam.sourceforge.net/](http://webcam.sourceforge.net/)

---

### Post by patrick295767 on 2006-02-22
------------------------------------
Sharing a folder in Windows for Linux :
------------------------------------
First, in windows: 
Right click on the folder to share:
(I hope u put for XP the advanced sharing in parameters :-) )
Plz check the two tabs in order to do ur sharing :
the first one : SHARING
the second one: SECURITY 
Put EVERYONE and ALL Things (read / write ... )
or one USER (yourusername / yourpassword)
(if you are in a limited network (no internet) ... )

Then, In Linux:

```
sudo bash
mkdir /mnt/mywindowsfolder
mount  -t smbfs //machinename/share /mnt/mywindowsfolder -o username=yourusername,password=yourpassword
```

---

### Post by patrick295767 on 2006-02-24
To Help the Video, to work better and also with mozilla-firefox:
---------------------------------------------------------
(script)

```
#!/bin/bash
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin 
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer

##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config
```
     
  Easy and rather fast to be done & installed
(check the ##never forget this for all the users)
   
 ------------  
dwl from the website: [http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner]("http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner")
(to install realplayer: 
chmod +x realplay.bin
./realplay.bin
& correct mv... and so on ...

---

### Post by patrick295767 on 2006-02-24
To Start a Script automatically or /etc/gdm stop (for instance)
--------------------------------------------------------------:
at specific time of the year, month, day .... and very easily :
---------------------------------------------------------------
   
1/ An easy one is Kcron
```
apt-get install kcron
```

2/ xterm, 
```
sudo kcron &
```

3/ set up what u need & want in kcron

4/ ```
sudo vi /etc/crontab
```
and add root to ur command ...
and, it'll work fine.
  
U may have a look to one working /etc/crontab (mine):
```
 #This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 * * * *	root	run-parts --report /etc/cron.hourly
# 
25 6 * * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
# 
47 6 * * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
# 
52 6 1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Please be informed tthat I am stopping gdm
0,30,55 0,23 * * *	**root	**/etc/init.d/gdm	stop
# Please be informed tthat I am stopping kdm
0,30,55 0,23 * * *	**root	**/etc/init.d/kdm	stop
# I start the gdm
0 7 * * *	**root	**reboot

# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```
(check that the bold root is present)
  
Instead of /etc/init.d/kdm stop
u can replace by it : /etc/init.d/mysupermegascript.sh
(chmod +x /etc/init.d/mysupermegascript.sh)

---

### Post by patrick295767 on 2006-02-24
UBUNTU Wiki: 
==========
  
How to install Ubuntu Linux on low memory systems (Pentium II and III Processor, 32-256 MB RAM)

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)
   
Ubuntu Lite exists too for old PC :-)
[www.ubuntulite.org/](www.ubuntulite.org/)

---

### Post by patrick295767 on 2006-02-24
My SERVER Installation for having a fast Desktop, fvwm with kicker bar:
=============================================
Slot in the CD installation, breezy, make a server install, change the /etc/apt/sources.list,

then, start the script & (reply first few questions) & have a cup of coffee ... 
When u'll be returned, it's installed.

```
#!/bin/bash
date
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
##cp "/root/.fvwm2rc" "/home/$1/.fvwm/.fvwm2rc"
apt-get -f -y install mc
apt-get update
apt-get -y upgrade
apt-get -f -y install mc proftpd
apt-get -f -y install nfs
apt-get -f -y install 
apt-get -f -y install ssh
apt-get -f -y install ftp
apt-get -f -y install openssh-server
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xorg
apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install fvwm 
apt-get -f -y install xlock
apt-get -f -y install xlockmore
apt-get -f -y install rox-filer
apt-get -f -y install leafpad
apt-get -f -y install xterm
apt-get -f -y install
apt-get -f -y install

apt-get -f -y install nfs-common
apt-get -f -y install nfs-kernel-server
apt-get -f -y install portmap
apt-get -f -y install nfs
apt-get -f -y install 
apt-get -f -y install autofs
apt-get -f -y install idesk
apt-get -f -y install xloadimage
apt-get -f -y install samba
apt-get -f -y install unzip
apt-get -f -y install bzip2
apt-get -f -y install gzip
apt-get -f -y install openssh-server

apt-get -f -y install growisofs
apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install 
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install nedit
apt-get -f -y install gedit
apt-get -f -y install gnome-chess
apt-get -f -y install menu
apt-get -f -y install debian-menu
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install xpdf xzgv 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip
apt-get -f -y install scrot
apt-get -f -y install gdesklets
apt-get -f -y install idesk
apt-get -f -y install krusader
apt-get -f -y install bootcd
apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install digikam
apt-get -f -y install audacity kaudiocreator
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install k3bsetup
apt-get -f -y install kate
apt-get -f -y install
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install imagemagick
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install kadu
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install dvd+rw-tools
apt-get -f -y install growisofs mozilla
apt-get -f -y install mozilla-firefox

## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install tcl8.4 sun-j2re1.5 flashplayer-mozilla
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

apt-get -f -y install gcc
apt-get -f -y install gcc-3.4
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 

apt-get -f -y install


apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install dvd+rw-format
apt-get -f -y install 
apt-get -f -y install imagemagick mozilla-browser
apt-get -f -y install gaim
apt-get -f -y install 

apt-get -f -y install opera
apt-get -f -y install nfs
apt-get -f -y install mozplugger
apt-get -f -y install kopete

apt-get -f -y install xlockmore
apt-get -f -y install kfmclient
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install kaffeine
apt-get -f -y install kadu
apt-get -f -y install xine
apt-get -f -y install

apt-get -f -y install gnome-volume-manager
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install vpnc
apt-get -f -y install kcron
apt-get -f -y install cron 
apt-get -f -y install libqt3c102-mt
apt-get -f -y install crond gpdf kpdf gs kghostview
apt-get -f -y install xzgv mplayerplug-in

apt-get -f -y install xmltv
apt-get -f -y install audacity gcc
apt-get -f -y install digikam kmail kaddressbook mtools annoyance-filter khelpcenter kleopatra
apt-get -f -y install nfs nfs-common
apt-get -f -y install libpt-plugins-v4l kmail
apt-get -f -y install kontact kmail
apt-get -f -y install kicker
apt-get -f -y install konsole gxine
apt-get -f -y install kmines 
apt-get -f -y install galeon
apt-get -f -y install minimo
apt-get -f -y install camorama kbear gftp
apt-get -f -y install klondike kdict
apt-get -f -y install kmahjongg
apt-get -f -y install kate grip
apt-get -f -y install synaptic alsamixergui
apt-get -f -y install synaptics
apt-get -f -y install wine gimp hatari 
apt-get -f -y install audacity
apt-get -f -y install ardour rezound ksim

apt-get -f -y install gweather
apt-get -f -y install gdesklets
apt-get -f -y install 

# hb
apt-get -f -y install libwxgtk2.4-dev
apt-get -f -y install tcltls planner kweather knewsticker korn wine





apt-get -f -y install xawtv
apt-get -f -y install gqcam qcam qc-usb-source qc-usb-utils
apt-get -f -y install 


echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer dgen xscreensaver xlockmore gnome-screensaver
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5
apt-get -f -y install azureus
apt-get -f -y install
apt-get -f -y install sun-j2sdk1.5
apt-get -f -y install
apt-get -f -y install
apt-get -f -y install azureus
apt-get -f -y install

echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
echo "** crossover is nice prg for windows apps**"
echo "fvwm" > "/home/$1/.Xsession"
echo "/home/$1/.Xsession"
echo "set up the fvwm as default"
apt-get -f -y install 



cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin 
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer

##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config



apt-get -f -y install xorg-driver-fglrx
## gatos also possible

######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin       #You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

## now the cedega
mkdir /root/patrickpackages
cd /root/patrickpackages

gzip -d cedega_4.4.3-1.i386.tgz
# un-tgz
tar -xvf cedega_4.4.3-1.i386.tar
## once done
##/usr created 
##you'll have to place it in /usr

tar -jxvf cdemu-0.7.tar.bz2.tar


############ antivirus
apt-get -f -y install build-essential
apt-get -f -y  install libwww-perl
apt-get -f -y  install libgtk2.0-dev
apt-get -f -y  install checkinstall

cd /root
dpkg -i xfprot*.deb

cd /root
tar zxvf xfprot-1.15.tar.gz
tar zxvf xfprot-1.15.tar.gz.tar

cd xfprot-1.15
./configure --with-gtk2 --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
make
checkinstall
dpkg -i xfprot*.deb

smeg

########################### end of patrick packages
apt-get -y remove numlockx
apt-get -f -y install openoffice.org
apt-get -f -y install inkscape
apt-get -f -y install openoffice.org-bin
apt-get -f -y install
apt-get -f -y install

############# End of Installing (long packages)
############# fr - nothg -nothg
echo "Please choose gdm "
apt-get -f -y install 
apt-get -y install gdm
apt-get -y install x-window-system-core
apt-get -f -y install xserver-xorg

apt-get -f -y install 
dpkg-reconfigure xserver-xorg
apt-get -f -y install 
apt-get clean
/etc/init.d/gdm restart


apt-cache pkgnames gnome 
date


echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"


```

---

### Post by patrick295767 on 2006-02-26
Plugging & mounting a device:
===========
Information concerning the USB: 
```

sudo tail -f /var/log/messages
```
  
or 

```
dmesg
```
(lsusb  too but not much nfo)
   
or eventually (may work also):
```
apt-get -f -y install qtparted 
qtparted &
```

---

### Post by patrick295767 on 2006-02-27
How to record your X11 screen (with mouse movements) via xvidcap :
===========================================
   
(via script)
1/ First, get the file : xvidcap_1.1.3-1_i386.deb and copy it to /root

2/ and run this script:
```
#!/bin/bash
echo "  " >> /etc/apt/sources.list
echo "## libavcodec1 " >> /etc/apt/sources.list
echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
cd /root
dpkg -i xvidcap_1.1.3-1_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"
```
  
  
3/ to record ur screen:
sh /root/xvid.sh
  
(rename the gz of the video to avi, once done)
(mplayer can play it)  
   
   
nfo:
*The MPEG file will be saved in your local directory. Using the default window size, about 150x75 pixels and capturing about 10 seconds worth of video produced a file size of only 28KB. Naturally, you'll probably want to do full screen captures. For that you'll need a decent Pentium 3 or 4 machine with lots of memory. My old 300 MHz, 256 MB laptop was wheezing, but it did work for the above example. *

   
Another installing way:
=================
>   $ wget [http://ovh.dl.sourceforge.net/sourceforge/xvidcap/xvidcap-1.1.3-p7.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/xvidcap/xvidcap-1.1.3-p7.tar.gz)
  $ tar -xzf xvidcap-1.1.3-p7.tar.gz
  $ cd xvidcap-1.1.3-p7
  $ ./configure --with-gtk2 --with-forced-embedded-ffmpeg
  $ make
  $ su
  # checkinstall
  # exit
  $ gvidcap
  
Additional informations:
==================
> La capture d'image par xvidcap : 


$ xvidcap --gui no --cap_geometry 1280x1024+0+0 --fps 10 --frames 0


Ceci commence la capture des images affichées à l'écran à la vitesse de 10 img/s pour une résolution de 1280x1024 à adapter suivant votre résolution. 
Les images sont enregistrées dans le dossier courant au format xwd (X window dump) non-compressé. Ici cela prend 5Mo/img soit 3Go/min. 
Les ressources demandées peuvent être diminuées en réduisant la surface d'écran capturée ou le nombre d'images par secondes. 


La conversion des images : 

mencoder ne gère pas le format xwd, on va donc convertir les images produites par xvidcap dans le format png avec convert de ImageMagick. 
convert ne prend qu'un seul fichier en entrée, il faut donc l'executer pour chaque fichier à convertir, pour cela on utilise le script shell suivant : 


#!/bin/sh 

for f in ${PWD}/*.xwd ; do 
convert $f $f.png && rm -f $f 
echo $f 
done

Celui-ci execute convert pour chaque image xwd puis efface cette dernière et affiche le chemin de l'image traitée. 
Attention : Les lignes de fin de ce script doivent être de type "LF" (ou '\n') et non "CRLF" (ou "\r\n") car sh ne gère pas ce dernier type. 

Ici le script est nommé 'mycap.sh' et se trouve dans le même dossier que les images à convertir : 


$ sh mycap.sh


Production d'une vidéo avec mencoder : 


$ mencoder mf://*.png -ovc rawrgb -o video.avi

Ceci produira une vidéo au format avi à partir des images png précédemment obtenues. 
Référez vous à la page man de mencoder pour utiliser un codec plus adapté que rawrgb (pas de compression). 


vbnul
   
If you'd like to have a swf format instead of avi:
====================================
[http://www.unixuser.org/~euske/vnc2swf/(](http://www.unixuser.org/~euske/vnc2swf/()...)
  
or use of : [http://www.cs.ubc.ca/~bsd/vncrecording.html](http://www.cs.ubc.ca/~bsd/vncrecording.html)
(vnc -> avi   via transcode)
   > vncrec -record file.vnc :0
transcode -x vnc -y xvid -i file.vnc -o file.avi -z -k
$ Xvnc :1 -once -depth 16 -geometry 1600x1200 &
$ DISPLAY=:1 transcode -i vnc ...
   
(Recording audio: mplex -f 8 -O 500 test1.mp2 test1.mov -o test.vob )

---

### Post by patrick295767 on 2006-02-27
Script on ur files in ur folder via ls
=====================

```
        #!/bin/bash
        for i in $( ls ); do
            echo item: $i
        done
```

find more there: [http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#s7](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#s7)

---

### Post by patrick295767 on 2006-02-27
How to install & work via  VPN / VPNC :
=======================

to install it : 
```
apt-get -f -y install vpnc 
```

or: [http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/)

If you have 5.04 ubuntu:
1) Install vpnc
2) gedit /etc/vpnc.conf :
Interface name vpnlink
IPSec gateway IP_address
IPSec ID ipsecclient
IPSec secret secret_code
Xauth username yourusernam
3) start vpn : sudo vpnc-connect
4) stop vpn : sudo vpnc-disconnect


If you have 5.10 ubuntu:
1) Install vpnc

if no internet to install it
[http://packages.ubuntu.com/breezy/net/vpnc](http://packages.ubuntu.com/breezy/net/vpnc).
sudo dpkg -i /pad/naar/vpnc-pakket
2) sudo nano /etc/vpnc.conf:
Interface name vpnlink
IPSec gateway IP_address
IPSec ID ipsecclient
IPSec secret the_secret
Xauth username your_username
3) start vpn : sudo vpnc
4) stop vpn: sudo vnpc-disconnect

Greetings,

Patrick

---

### Post by patrick295767 on 2006-03-05
for new linux users: 
==============
```
30 is the number of directories starting from the largest. 
=================================================== 
Backup the dir's on a server run the following from /: 

Tar -cfz /dir/filename.tgz /var/qmail/ /etc 

Verify file is in /home and correct size/date. 
Tar and Gunzip 
Tar switches /source/ destination 

1. Compress. Tar &#8211;cvzf filename.tar.gz /sourceoftar 
Tar &#8211; cvzf etc.tar.gz /etc 

2. Decompress 

gunzip filename.tar.gz 
gunzip etc.tar.gz 
or 
tar &#8211;xf etc.tar 
===================================================== 
RPM's (Redhat Package Manager) 

To install a package: rpm &#8211;ivh 
ex. rpm -ivh somepackage.1.1-4.i386.rpm 

To upgrade a package: rpm -Uvh [filename] 
ex. rpm -Uvh somepackage.1.1-5.i386.rpm 

To remove a package: rpm -e [packagename only no .rpm or version number] 
ex. rpm -evh somepackage 
===================================================== 

To see if a package is installed: rpm -q [packagename] 
ex. rpm -q somepackage 
Rpm &#8211;q webadmin 
===================================================== 

To get info on an installed package: rpm -qi [packagename] 
ex. rpm -qi somepackage 
===================================================== 
Disk free space 


df amount of free disk space df &#8211;I by drives 
===================================================== 
Disk usage 

du amount of used disk space du &#8211;s or du -s* 
===================================================== 
Date 

Date shows/sets current date date MMDDhhmmYYYY (sets date/time) 
===================================================== 
Who is online 

Who users currently on system 
===================================================== 
Free 

Free how much RAM and cache is free 
===================================================== 
Who is online 

w users online and what files are being used 
===================================================== 
Touch 
```
   
    
Which CPU u have & details :
```
cat /proc/cpuinfo
```

Hardware and details about ur video card:
```
lspci
```
   
> sudo lshw give's a list of your computer hardware
> lspci gives a huge list of components in your machine.
> cat /proc/cpuinfo will tell you about your CPU.
> cat /proc/meminfo tells abou memory.

---

### Post by patrick295767 on 2006-03-13
How to physically recognize Ethernet Crossover or Straight Cable (colors) :
--------------------------------
[http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp](http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp)

---

### Post by patrick295767 on 2006-03-13
DVD to DIVx:
-------------
```
apt-get -f -y install acidrip 
```


to RIP cd-audio:
---------------
```
apt-get -f -y install grip
```

---

### Post by patrick295767 on 2006-03-13
Nice How to Dual Boot Ubuntu:
-------------------------------
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by patrick295767 on 2006-03-23
DVD ripping:
==========

> This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

To make an ISO from files on your hard drive, create a directory which holds the files you want. Then use the mkisofs command.

mkisofs -o /tmp/cd.iso /tmp/directory/

This results in a file called cd.iso in folder /tmp which contains all the files and directories in /tmp/directory/.

For more info, see the man pages for mkisofs, losetup, and dd, or see the CD-Writing-HOWTO at [http://www.tldp.org](http://www.tldp.org).

Hope it helps
Sniff.
  

DVD ripping, Programs: 
================
dvd::rip    dvdrip
[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)
   
Acidrip
  
sudo apt-get install thoggen
[http://thoggen.net/](http://thoggen.net/)
Screenshots: [http://thoggen.net/screenshots/](http://thoggen.net/screenshots/)
     
In another thread someone raved about tovid. The website
[http://tovid.berlios.de/en/index.html](http://tovid.berlios.de/en/index.html)
      
maybe k3b for ripping ??
=========
Video convertions:
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)
    
   
DVD double layers to DVD mono layers: wine & dvdshrink
============
wine & dvd shrink:
How to:
[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
   
speed windows eg: 13,000 kbs 
speed into linux 10,000 kbs
abnormal speed in linux : 4,400 kbs
> If you already have it installed, hit alt-f2 and run the command 'winecfg'. This will bring up the new winecfg panel.

In the applications tab click on 'add appplication' and navigate your way to the dvdshrink .exe. Then set the windows version to 'windows xp' for dvdshrink.
Click on the drives tab and let it autodetect your drives.
Close winecfg and start dvdshrink again and the ASPI error should be gone.

The other problem you're going to have is a that the compression rates won't work properly when you open a disc for analysis. What I am doing at the moment is copying the whole dvd to the hardrive using dvdbackup. It's a command line program but works really well. Once installed you can use this command to backup the whole disc to your home directory

dvdbackup -i /dev/dvd -o /home/yourusername/ -M

I then choose 'open files' in dvd shrink and it is able to analyse the files from the hard disc (created by devbackup) properly and backup in the usual way. I usually backup to an iso image then burn with nautilus or k3b. by manicka
    
> HOW-TO: Install DVD Shrink with Wine in Breezy

This how-to will install DVD shrink with the new beta version of wine (0.9) from WineHQ. The version of Wine that comes with breezy will install DVD Shrink but will not analyse your original dvd's properly. As always check the relevant copyright laws for your country re backup of DVD's.

I'm assuming that you already have libdvdcss2 installed so that you can play your retail dvd's. If not follow the how-to here

PLF
[edit]
Installing Wine

The new Beta (0.9) release is now valiable at WineHQ and fixes a major bug with the preview window in DVD Shrink. Please use the WineHQ deb in preference to the version that comes with breezy -

Run

sudo gedit /etc/apt/sources.list


add these two lines two your souces.list

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/ 
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/


now update and install wine

sudo apt-get update
sudo apt-get install wine

[edit]
Configuring Wine

alt-f2
winecfg

This will setup your wine directories in ~/ and start the winecfg control panel

Once the winecfg control panel starts, go to the 'Drives' tab and allow it to autodetect your drive setup, by clicking on the 'Auto Detect' button. Close winecfg

N.B. some users have found that DVD Shrink is not detecting their drives properly. This advice from fergus may help:

By default, when you add a drive to wine it thinks its a hard drive and not a cd-rom. Try going into winecfg and to the devices tab. Then enable the Advanced options and select your dvd drive. It might be listed as a hard drive, change that to cd-rom and then DVD Shrink should pick it up.

Further advice.

Recently I did a fresk wine install by deleting my wine directory and then recreating my wine directory and installing dvd shrink again. I to ran into the 'drive not being detected' problem. A solution which worked was to download and install the latest version of winetools and use this to setup my basic wine configuration instead (after installation use the command '/usr/local/winetools/wt0.9jo' instead of 'wt' to start winetools). I would suggest using Winetools to create the fake windows directory, install arial font, install dcom98.exe and Microsoft Foundation Classes 4x. Winetools will also install IE6sp1 but I would not recommend installing this piece of junk.

IE6 will also mess up the way that dvd shrink runs (surrounding screen turns black) if ie6 is installed as well, so do yourself a favour and give it a miss. Once you have created a base setup using Winetools, you should be able to install dvdshrink as per the rest of this how-to.... enjoy
[edit]
Installing DVD Shrink

Download the DVD Shrink installer. The current version is 3.2.015 and you'll need to do a Google search (try DVD Shrink download) to find it, as the main site no longer carries links to the installer.

In a terminal in the directory that you downloaded DVd Shrink to, run the command

wine dvdshrink32setup.exe 

(or whatever the exe file is called)

Follow the installer instructions to install. At the end of the installation uncheck the box that asks to run DVD Shrink now.

when the installer is finished run

alt-f2
winecfg

This will start the winecfg panel again as we have to configure it to run DVD Shrink properly

In the Applications tab window click on 'Add application'

Navigate your way into Program Files-->DVD Shrink and find 'DVD Shrink 32.exe'

highlight this file and click on the open button.

This will now take you back to the Applications Tab window and DVD Shrink should appear in the list in that window.

Highlight DVD Shrink then go down to the Windows Version box and choose 'Windows XP' from the drop down menu.

Click on the 'Apply' button then OK to exit winecfg.


[edit]
Starting and Using DVD Shrink

The installer should have created an icon on your desktop. You can use this to start DVD Shrink or type the following command in a terminal

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

You can also use this command to make an entry in the Gnome menus with Smeg


Enjoy!  
  
I would recommand also to : 
do :
xterm
winecfg
then, do a AUTODETECT for cdroms and so on, once you have added 
"C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"
in order to get and make available the DVD drive

it Works great !
  
=========
A dvdshrink native for linux exists !
find the rpm, and make use of alien
  
---
Other programs:  K9copy   (in the repos)
xdvdshrink

---

### Post by patrick295767 on 2006-03-26
Playing with fvwm , .Xclients and xset function (screensaver, keys , ... )
================
from:[http://limestone.uoregon.edu/woven/RedHat/Custom-X-Tips-5.html](http://limestone.uoregon.edu/woven/RedHat/Custom-X-Tips-5.html)
> . Customizing the X Server

The ``X server'' is the program that knows how to draw windows on your screen, read keypresses from the keyboard, and read points, clicks, and drags from the mouse. All of these parts together are called the ``X display''. The X server allows some degree of customization of the display using the xset program.
5.1 Changing X Display Settings

Some of the settings you can change using `xset' are:

    * the ``beep'' setting
    * mouse acceleration
    * the builtin screensaver

Turning the Beep On or Off

If you don't want the X display to beep (for instance, when you send a control-G or ``bell'' character to xterm), you can turn it off using:

xset b off

to turn the beep on, use:

xset b on

Mouse Acceleration

If you want to ``accelerate'' mouse motion (so that you don't have to move the mouse very far to move the cursor from one edge of the screen to the other), you can change the acceleration:

xset m <multiplier>

<Multiplier> is a number (such as `4' or `3/2') such that, when you move the mouse fast, it travels that many times further than normal.
The Default Screensaver

If you want the builtin screensaver to come on after a certain amount of inactivity, you can turn it on or change the time period that it waits. To turn on the screensaver, use the following command:

xset s on

To make sure the screen is blanked, use:

xset s blank

To change the number of seconds after which to activate the screensaver, use:

xset s <number-of-seconds>

Notes and Pointers

NOTE that these settings will only affect the current X Windows session. If you want to change the settings every time you use X Windows, put the commands in your .Xclients script (you don't need to run xset in the background).

See the manual page for xset for more information.
5.2 Changing Root Window Settings

In X Windows, the ``root window'' is the first window that gets created; all other windows get drawn on top of it. In effect, the root window acts as a ``backdrop'' for your X session.

The root window has several properties that you can change to suit your taste:

    * the color of the root window
    * the shape of the mouse cursor

Root Window Color

To set the color of the root window to gray, use the following command:

xsetroot -gray

To set the color of the root window to any solid color, use the following command:

xsetroot -solid <color>

<Color> is either the name or the hexadecimal value of a color. For example, both of the following are equivalent:

xsetroot -solid white
xsetroot -solid '#ffffff'

You can find names of colors in the ``RGB database'', located in /usr/X11R6/lib/X11/rgb.txt.
Mouse Cursors

You can change the shape of the mouse cursor when it is above the root window (this doesn't change the cursor when it is above other windows) using the following command:

xsetroot -cursor_name <cursorname>

<Cursorname> is one of the ``standard'' X Windows mouse cursor shapes. Here is a list of some interesting ones to try out:

xsetroot -cursor_name draped_box
xsetroot -cursor_name hand1
xsetroot -cursor_name hand2
xsetroot -cursor_name iron_cross
xsetroot -cursor_name left_ptr
xsetroot -cursor_name plus
xsetroot -cursor_name top_left_arrow
xsetroot -cursor_name watch

In fact, you can use this feature of xsetroot in your .Xclients script to show a watch cursor while your clients are starting up, and then change it to a cursor of your liking just before the end of the script. For example:

#!/bin/sh
#
# .Xclients:  startup script for X Windows
#       
# show a watch cursor to indicate 
# that we're starting things up
xsetroot -cursor_name watch
#
# start clock
xclock &
#
# (other X clients here)
#
# change to a regular pointer to show 
# that we're ready for use
xsetroot -cursor_name top_left_arrow
#
# and finally, start window manager
exec fvwm
#
# -------- End of .Xclients --------

The full list of cursors is available in the X Windows include file /usr/X11R6/include/X11/cursorfont.h; each cursor shape is called XC_<cursorname>---you should leave off the XC_ prefix when using these names with xsetroot.
Notes and Pointers

NOTE that, much like xset the above commands will only affect the current X Windows session. If you want to change the settings every time you start X Windows, put the commands in your .Xclients script (you don't need to run xsetroot in the background).

For more information, see the manual page for xsetroot. For information about putting color graphic pictures (``wallpaper'') in the root window, see the manual page for xv (from the xv package) and xpmroot (from the fvwm package).

---

### Post by patrick295767 on 2006-03-30
Mounting the Share (smbfs share)
=========================
To mount an smbfs share from a Linux workstation at the command line, you can use either the smbmount command or use mount -t smbfs. Both command will work the same. When you use mount -t smbfs, the mount program actually passes the command over to smbmount for execution. Throughout this document I'll use smbmount instead of mount -t smbfs. 
An example would look like this: 
```
smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```
The mount equivelant is: 
mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```
//servername/sharename
``` refers to the name of the Windows computer and the name of the share. 
```
/mountdirectory
``` refers to the directory you use as the mount point on the Linux workstation. It can be any directory as long as the user executing the command has rights to it. 
Whether you need to supply a username and password depends on what type of security you have on the Windows share. If you have a share created with no password on it, you shouldn't need to provide a username and password. If the share happens to be on a Windows NT server that is part of a domain, you would need to provide a domain login name and password.

---

### Post by patrick295767 on 2006-04-02
Some HOW TO LINUX :
===================
> Table of Contents
1. Introduction
2. Initial install
3. Adding more software repositories
4. Installing applications
5. Installing and configuring SSH server
6. Configuring sound
7. Configuring login screen
8. Configuring X
9. Installing VMware Workstation
10. Installing VMware Player
11. DMA settings
12. Configuring firewall
13. Useful links

====> [http://users.piuha.net/martti/comp/ubuntu/install.html#5](http://users.piuha.net/martti/comp/ubuntu/install.html#5)

---

### Post by patrick295767 on 2006-04-02
HOW TO INSTALL VMWARE  Workstation Linux 
=============================
     
  
1/ start thsi script:
```
#!/bin/bash
## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
export CXX=/usr/bin/g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
```


2/
(let s be sure):
#type :
  
```
export CC=/usr/bin/gcc-3.4
```
  
  
3/ now, the VMware :
Forget about VMware-workstation-4.5.2 (I think it's working only with Hoary if i recall well)

You should have minimum :
VMware-workstation 5.0.0 for linux
===> so, Unpack VMware-workstation 5.0.0 for linux in your /root (for instance)

4/ run:
Code:
```

./vmware-install.pl
```


5/ press Enter all time (once you'll have to reply and type YES)

6/ done !!

7/ Enjoy

---

### Post by patrick295767 on 2006-04-08
LINUX server: Default  NFS & Router - static IP or DHCP?  
=========================
   
1/ make sure all installation of linux boxes are DHCP
  
  
2/Now configure your server linux:
The router is configured so that he is looking/checking the MAC addresses and giving one IP static to the server.

That's very easy this way and gives less troubles !

Greeetz

---

### Post by patrick295767 on 2006-04-09
How to have polish english dictionary YDPDict:
===============================
  
1/ first: 
```
apt-get -f -y install ydpdict luit  konsole gedit wine 
```
  (it's in the repos') (check your /etc/apt/sources.list if you have problems)
  
2/```
 mkdir /opt
mkdir /opt/ydp
mkdir /opt/ydp/database
```

3/ install the original program made for windows (you could use wine also)
```
Install the YDPDICTwindows program from the original cd to get the dat and idx files ...==> wine or with windows 
```
 
```
cp /dos/WinProg/Ydp/database/dict*.dat /opt/ydp/database
cp /dos/WinProg/Ydp/database/dict*.idx /opt/ydp/database
```


4/ the goal of the point (3)/ is to get this ready:

enter : 
```
cd /opt/ydp/database
ls -la 
```

and check you have this : 
> /opt/ydp/database$ ls -la
total 11960
drwxr-xr-x  2 root root    4096 2006-04-08 21:44 .
drwxr-xr-x  3 root root    4096 2006-04-02 19:45 ..
-rwxr-xr-x  1 root root 6389018 2006-04-02 19:46 dict100.dat
-rwxr-xr-x  1 root root  465714 2006-04-02 19:46 dict100.idx
-rwxr-xr-x  1 root root 4876978 2006-04-02 19:46 dict101.dat
-rwxr-xr-x  1 root root  470984 2006-04-02 19:46 dict101.idx
Take care, the names of the files dict100* should be lowercase !!
  
5/ now, :
type : 
```
gedit /etc/ydpdict.conf
```
  
and make sure the folder /opt/ydp/database is there !! 
(my conf file:
```
# cieka prowadzca do plik&#65533; sownika. Uwaga: dost&#65533; do plik&#65533;
# umieszczonych na partycji FAT lub VFAT jest w wypadku jder 2.0.x znacznie
# wolniejszy ni do plik&#65533; na partycji EXT2.

#Path /usr/local/share/ydpdict

Path /opt/ydp/database

# cieka prowadzca do katalog&#65533; z pr&#65533;kami dwi&#65533;owymi.

CDPath /mnt/cdrom

# cieka do programu odtwarzajcego pr&#65533;ki dwi&#65533;owe (play lub mpg321).
# Jeeli nie jest ustawiona, program pr&#65533;uje sam odtworzy&#65533;pr&#65533;ki.

#Player play
#Player mpg321

# Zestaw znak&#65533;, z kt&#65533;ego korzysta program: None (bez polskich liter),
# ISO-8859-2 (polskie litery), Unicode (polskie litery i transkrypcja
# fonetyczna przy odpowiedniej czcionce). Mona te uy&#65533;parametru UnicodeSet,
# a wtedy program sam przeczy konsol&#65533;w tryb UTF-8.

Charset ISO-8859-2

# Wprawdzie program potrafi wykrywa&#65533; czy terminal obsuguje kolory czy nie,
# to jednak mona wymusi&#65533;ich wywietlanie lub ich brak.

UseColor On

# Tryb z przezroczystym tem lub bez

UseTransparent On

# By zmieni&#65533;kolory wywietlanego tekstu naley zmieni&#65533;ponisze wartoci
# na jedne z nast&#65533;ujcych: Black, Red, Green, Brown, Blue, Magenta, Cyan,
# White, Gray, Yellow, LightRed, LightGreen, LightBlue, LightMagenta,
# LightCyan, LightWhite. Uwaga: dla kolor&#65533; z przedrostkiem "Light"
# pogrubienie tekstu nie b&#65533;zie widoczne.

# Kolor tekstu
```

6/ this is done, almost soo now, 
(we need a freshly started konsole)
you need to type in an xterm or aterm ... :

```
konsole -e luit -encoding iso-8859-2 ydpdict
```
  
7/ in case you get some troubles, plz do: 
```
killall -9 -e ydpdict
killall -9 -e luit
konsole -e luit -encoding iso-8859-2 ydpdict
```

That's working !!
Enjoy !!  
  
  Patrick295767
  
====
References:
[http://toxygen.net/ydpdict/](http://toxygen.net/ydpdict/)
[http://www.linux.sky.pl/teksty/ydp.html](http://www.linux.sky.pl/teksty/ydp.html)

---

### Post by patrick295767 on 2006-04-09
Soo today : 
==================================
How to install Kydpdict (KDE apps) [http://members.elysium.pl/ytm/gfx/kydpdict-scr5.png](http://members.elysium.pl/ytm/gfx/kydpdict-scr5.png)
==================================
  
1/  install ydpdict ; look my previous post HOWTOINSTALL YDPDICT

2/ Make sure the /etc/ydpdict.conf is correct and you have :
```
 /opt/ydp/database$ ls -la
total 11960
drwxr-xr-x 2 root root 4096 2006-04-08 21:44 .
drwxr-xr-x 3 root root 4096 2006-04-02 19:45 ..
-rwxr-xr-x 1 root root 6389018 2006-04-02 19:46 dict100.dat
-rwxr-xr-x 1 root root 465714 2006-04-02 19:46 dict100.idx
-rwxr-xr-x 1 root root 4876978 2006-04-02 19:46 dict101.dat
-rwxr-xr-x 1 root root 470984 2006-04-02 19:46 dict101.idx
```
  
3/ So now, : 

```
echo " " > /root/myscriptydpdict.sh
gedit /root/myscriptydpdict.sh
```

copy paste this  content :
```
#!/bin/bash

## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 

## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
apt-get -f -y install
apt-get -f -y install

######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt

## dictionaruies
# ydpdict
apt-get -f -y install ydpdict 
apt-get -f -y install konsole
apt-get -f -y install luit
#
apt-get -f -y install kydpdict
apt-get -f -y install gdict
apt-get -f -y install 
## since kydpdict is not in the repos...
##let's make it work
export QTDIR=/usr/share/qt3
export QTDIR=/usr/share/qt3
cd /root
wget http://members.elysium.pl/ytm/src/kydpdict-0.9.0.tar.bz2
tar -xjf kydpdict-0.9.2.tar.bz2
cd kydpdict-0.9.2
./configure
make
make install
cd /root
###wget http://..../ydpdict.conf
##cp ydpdict.conf /etc/ydpdict.conf
## done man !!
cd /root



```

then:
 ```

chmod +x /root/myscriptydpdict.sh
cd /root
./root/myscriptydpdict.sh 
```


  
That's installed !!!

```
xterm
kydpdict &
```

---

### Post by patrick295767 on 2006-04-09
How to start/run a script: 
==============
```
sudo bash
apt-get -f -y install gedit 
echo " " > /root/myscriptydpdict.sh
gedit /root/myscriptydpdict.sh
```
    
u can then copy paste the script code...
then:
   
```
chmod +x  /root/myscriptydpdict.sh 
cd /root
./myscriptydpdict.sh 
```

Greetings

---

### Post by patrick295767 on 2006-05-05
How to record RealAudio/streaming media? 
========================
1)Dump the stream to your PC
Code:
 mplayer -playlist your real stream url -dumpstream -dumpfile output.ram
2) Convert the dump to a WAV file.
Code:
mplayer pov -ao pcm:file=file.wav 
3) Convert to WAV to mp3.
Code:
lame -f file.wav filem.mp3
 
Thanks !

---

