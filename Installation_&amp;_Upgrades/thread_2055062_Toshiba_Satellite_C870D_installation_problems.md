---
title: "Toshiba Satellite C870D installation problems"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by Kepu on 2012-09-08
I have new Toshiba Satellite C870d laptop, tried install several times Ubuntu 12.04 Lts,
from LiveCD and several times with Windows installer (Wubi)
But it always freeses to some point 
From LiveCD it boots up but when I try to install it goes well and everything seems to work fine untill about 90% is done then installation seems to freese,  screen is fine, mouse does not work, and nothing happends (Waited over half hour cople times.
From Windows intallation  (Wubi) it has gone through couple times (6 times not gone through) , but when I boot from hardrive it freeses same way very quickly after few 10 seconds mouse not working and everything just standing on screen like waiting something.
Any idea what to try , Please Help
My small Toshiba netbook worked fine, but this bigger laptop does not.

   My Laptop is  
 AMD E2-1800 pros,
 640GB harddrive,
 4GB DDR3 SDram,
 AMD Radeon HD 7340 Graphics,   17.3" screen
HDMI, USB2, USB3, Ethernet, Wifi
 Window s 7 Home Premium 64bit

---

### Post by oldfred on 2012-09-08
Welcome to the forums.

Some have had this issue?

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by Kepu on 2012-09-08
Thanks for response.

I got it installed with wubi and ubuntu 12.04 32bit package,
 but installation is not 'stable', 
laptop is freezing randomly in 5 to 10 minutes after boot ,
 ( or sometimes during boot).  
I can't see any connectios with those) ,  freezing happen same way 
as it was happening  during installation :

Mouse and keyboard stop working and screen stands on,
needs reboot by taking power cord and battery off .
otherwise ubuntu seems to work fine, 
Please, Any suggestions, I am novice with linux  

Also I didn't get wireless to work yet - I already downloaded Realtec driver , 
but I should get Ubuntu work stable first

wireless might start to work  when I first try to connect laptop to 
internet with wire to get  'sudo install build-essential'  to work
 (there was something missing)  before compiling wireless driver

---

### Post by oldfred on 2012-09-08
Random is the worst thing to try to resolve.

I would look into log files. You can use Log File Viewer. I start with dmesg but it may be any of the other devices.

---

### Post by Kepu on 2012-09-09
Now a little more info about the problem ,
It might be related somehow my laptops 'power saving system' , 
because screen is going in very short time to saving mode ( meaning it's brightness
is going to a little bit  lower lever), and then again later whole laptop is going to sleep ,
even in Windows when I was downloading ubuntu package I had to be all  the time on front of laptop for moving mouse time  to time otherwise I notice that, downloading stopped too, (it continues in few seconds after awakening .
I tried already to change those times in Windows, but it didn't seam to work, not even in Windows.
And now in Ubuntu I noticed that, if I keep screen  'busy' by moving mouse time to time  for example during  installation of applications , -installation does not fail,
ubuntu worked  yesterday evening 4 hours fluently without freeze , (  I installed Wine, Winetricks, Seamonkey, Kongueror ) and got wireless working after  2 hour trying,
 (I used info from : 
[http://blogs.fsfe.org/stefan.a/2011/06/14/how_to_install_realtek_rtl8188ce_wifi_drivers_thinkpad_edge_13_on_ubuntu_natty_1104/](http://blogs.fsfe.org/stefan.a/2011/06/14/how_to_install_realtek_rtl8188ce_wifi_drivers_thinkpad_edge_13_on_ubuntu_natty_1104/)
and now I have been online 2 hours just have to make sure that something is happening all time.
Now the biggest problem is freezing during boot, first freezing point in boot is when
Ubuntu text with dots is on screen and second point sometimes just immediately after password typing .
 I noticed after choosing Ubuntu from dual boot screen and before linux kernel version 
screen, there is in fraction of second rolling some text and last one is error message, but it is so short time on screen  - I have not be able to read it
I hope this help you guys to quide me  !

---

### Post by oldfred on 2012-09-09
Does your BIOS have a screen saving or power saving setting?

---

### Post by Kepu on 2012-09-09
Sorry , I have no glue  how to check that

 :(

---

### Post by oldfred on 2012-09-09
Do you have a manual for your system? If not download one from the vendor. 

You can often get to BIOS with del key, f2 or other, but it varies by vendor. Boot screen should flash for a second and show what key to use.

---

### Post by Kepu on 2012-09-10
Thanks!
I found in setup / prosessor power setting/ [dynamic] versus [always low]
It was in default [dynamic] meaning power lever changes all time depending 
of processor usage to keep speed high.
I change it to [always low] so processor runs always on same power lever 
(suppose, a little bit lower than speed than other one) .
I have booted now 3 times with no problems and I haven't noticed any 
speed problem with programs what I am mostly using
 (although  it might be different story with  games, but this not any way 
meant to be 'The ultimate game machine'
I will test more tomorrow, it is so late now , and I will inform if problem is solved.

---

### Post by Kepu on 2012-09-12
OK, thanks Oldfred your help!
Problem was in processor power setting, 
after changing  [dynamic] to [always low]  , there was no freezes any more.
And actually computer still runs normal speed.
So problem is solved.

---

