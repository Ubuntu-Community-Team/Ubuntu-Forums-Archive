---
title: "kernel 2.6.39.0 is not on my list, how do i get 1 on the list?"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by TweFoju on 2011-09-30
so, with the 11.04 keep crashing randomly and all, i learn that you need to upgrade the Kernel

like in many website suggested we do the following:

> 
sudo add-apt-repository ppa:kernel-ppa/ppa  sudo apt-get update> 
apt-cache showpkg linux-headers
and finally

> 
sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing
but the problem is, the 2.6.39.0 Kernel is not on the list, thus, it's useless to do the last command

question is, how do i make it appear on the list?

any command?

i searched anywhere on google, no one seems to have answer for it, i hope i can solve it here 

thanks! :(

here's the LOG:

> 
wils@Twe:~$ sudo add-apt-repository ppa:kernel-ppa/ppa
[sudo] password for wils: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 800AA67AE64A6D9E1859C561A8267963484B044F
gpg: requesting key 484B044F from hkp server keyserver.ubuntu.com
gpg: key 484B044F: public key "Launchpad PPA for Ubuntu Kernel PPA" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
wils@Twe:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty InRelease                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates InRelease             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release.gpg           
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release                        
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,744 B]                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Sources                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main amd64 Packages           
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [14 B]             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe amd64 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse amd64 Packages     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Sources                
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages [14 B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en_CA                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en_CA            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_CA            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_CA 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 10.1 kB in 2s (3,592 B/s)                       
Reading package lists... Done
wils@Twe:~$ apt-cache showpkg linux-headers
Package: linux-headers
Versions: 

Reverse Depends: 
  oss4-dkms,linux-headers
  lirc-modules-source,linux-headers
  bcmwl-kernel-source,linux-headers
  xtables-addons-dkms,linux-headers
  oss4-dkms,linux-headers
  openswan-modules-source,linux-headers
  lirc-modules-source,linux-headers
  blcr-dkms,linux-headers
  alsa-source,linux-headers
  nvidia-current,linux-headers
  nvidia-96,linux-headers
  nvidia-173,linux-headers
  fglrx,linux-headers
  bcmwl-kernel-source,linux-headers
  dkms,linux-headers
Dependencies: 
Provides: 
Reverse Provides: 
linux-headers-2.6.38-11-virtual 2.6.38-11.50
linux-headers-2.6.38-11-server 2.6.38-11.50
linux-headers-2.6.38-11-generic 2.6.38-11.50
linux-headers-2.6.38-11 2.6.38-11.50
linux-headers-2.6.38-10-virtual 2.6.38-10.46
linux-headers-2.6.38-10-server 2.6.38-10.46
linux-headers-2.6.38-10-generic 2.6.38-10.46
linux-headers-2.6.38-10 2.6.38-10.46
linux-headers-2.6.38-8-virtual 2.6.38-8.42
linux-headers-2.6.38-8-server 2.6.38-8.42
linux-headers-2.6.38-8-generic 2.6.38-8.42
linux-headers-2.6.38-8 2.6.38-8.42
wils@Twe:~$ 


---

### Post by MAFoElffen on 2011-09-30
> **TweFoju said:**
> so, with the 11.04 keep crashing randomly and all, i learn that you need to upgrade the Kernel

like in many website suggested we do the following:

and finally

but the problem is, the 2.6.39.0 Kernel is not on the list, thus, it's useless to do the last command

question is, how do i make it appear on the list?

any command?

i searched anywhere on google, no one seems to have answer for it, i hope i can solve it here 

thanks! :(

here's the LOG:
[COLOR=Red]I have that info for you "if" you "really" want to do that[/COLOR], BUT... You really might want to check the dates of your web resources and the "WHY's" they recommended that.

Let me explain a few things why I said that: (As I remember)

Linux 2.6.39~rc1 thru ~rc4 (for natty) came out while we where testing Natty <> 2.6.28.8 was adopted for  the Natty Release...  2.6.39~rc4 is older (APR 2011) than 2.6.38.8 (release version, JUN 2011).  Current for Natty today is 2.6.38.11. I believe natty proposed currently has 2.6.38.15.

2.6.39.0 Oneiric (May 2011) went on in Onieric testing, but the release in a couple weeks will be with 3.0.x... (better)

You could "compile" linux kernel 3.0.x for Natty but would you have to apply other patches also...

So why would you want to install an old kernel version that had issues in natty testing, that were worked on later in the Linux 2.6.38.x series?  Just curious...

EDIT-- [COLOR=Red]
NOTE[/COLOR]: Is the same instructions as garvinrick4 already gave in post #4

---

### Post by garvinrick4 on 2011-09-30
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Pick out the kernel you want from above and click on it will give you downloads available. 
Already built in .deb

So download the .all deb
download the headers (in your 32 or 64 bit whichever you run) uname -a (in terminal)
download the image (in your 32 or 64 bit whichever you run)

Now just click on them in the order you downloaded them (3 of them) as above and they will install through Ubuntu software center the kernel you desire, 2.6.39 is in the list.

Now in upper upper right corner of Ubuntu Forum page you will see a launchpad.net
Click on that and join. And if you need a package in Ubuntu you can Google
for instance "launchpad network-manager in .deb" and you can get packages already
built (.deb) so as to be a able to install through software manager by clicking on. (do not have any compiling to do)

If any trouble in command line.
Lets say they are on Desktop the .deb package you just go to path:
```
cd Desktop
```see package
```
ls
```and install```
sudo dpkg -i (copy and paste package after space after i and hit enter will install.)
```If you are going to be a Ubuntu user it is nice to also be a Launchpad member and 
learn your way around launchpad.net is invaluable.

Below is link for software center that is in pdf format.
[Free Guide to the Ubuntu Software Center [Download] - How-To Geek ETC]("http://www.howtogeek.com/news/free-guide-to-the-ubuntu-software-center-download/6670/")

---

### Post by TweFoju on 2011-09-30
> **MAFoElffen said:**
> [COLOR=Red]I have that info for you "if" you "really" want to do that[/COLOR], BUT... You really might want to check the dates of your web resources and the "WHY's" they recommended that.

Let me explain a few things why I said that: (As I remember)

Linux 2.6.39~rc1 thru ~rc4 (for natty) came out while we where testing Natty <> 2.6.28.8 was adopted for  the Natty Release...  2.6.39~rc4 is older (APR 2011) than 2.6.38.8 (release version, JUN 2011).  Current for Natty today is 2.6.38.11. I believe natty proposed currently has 2.6.38.15.

2.6.39.0 Oneiric (May 2011) went on in Onieric testing, but the release in a couple weeks will be with 3.0.x... (better)

You could "compile" linux kernel 3.0.x for Natty but would you have to apply other patches also...

So why would you want to install an old kernel version that had issues in natty testing, that were worked on later in the Linux 2.6.38.x series?  Just curious...

EDIT-- [COLOR=Red]
NOTE[/COLOR]: Is the same instructions as garvinrick4 already gave in post #4
because they say it fixed the crash?

i dont know, i thought it's newer kernel because it's 39

anyway, if that kernel can make the crashing stop. why not the latest version?

because 38-11 still crashes sometimes even when im only browsing

does that happen to you guys with 38-11 ?

---

### Post by garvinrick4 on 2011-09-30
I use the 3.0 and up in Natty because my Network controller works better with that kernel
in Natty "iwlagn" driver from Intel.
If you go to 3.0 and up works fine here but do have to upgrade your
module-init-tools to 3.13 (below are .deb just have to choose your 32 or 64 bit.) (always check under "builds" that is where you find your .deb packages)
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

---

### Post by garvinrick4 on 2011-09-30
If you install a new kernel your old kernels will still be there to boot from in case the new
kernel hits the skids on you. Always keep known working kernels in you system to boot
from. I always keep 2 kernels of each install, never just one. Easy to remove kernels
through synaptic just type kernel in search window 2.6.38-11 for example. Kernels will
show in terminal with.
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by TweFoju on 2011-09-30
sorry man, im still not good with the Linux language 

so i went to the link you gave just now

and there are 3 download files, but none say which version, i am using 64 btw

so all in all

would you recommend me to upgrade to 3.xx? 

and if so, any available command that i can use do to upgrade from 2.6.38-11 ?

should i use this before i upgrade to 3.xx or after?

grep menuentry /boot/grub/grub.cfg
thanks..

---

### Post by garvinrick4 on 2011-09-30
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/")
The bottom 5 now take only 3 of them. (1 all.deb and 2 with amd64 )
Download the all.deb
Download Linux headers amd64.deb
Download the Linux image amd64.deb
Download them to lets say Desktop or Downloads where ever you know where to find them.
Will be 3 .deb packages there.
Just click on each one just as I have listed 
all.deb
headers
image
They will install and you have a new kernel. 2.6.39

If any errors just let me know what it says, should go smooth though.
If for any reason it says need module-init-tools 3.13
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500)
In the lower left it ends in .deb
Download it and click on it, will install on its own. If it does not ask do not worry about
you are done.

---

### Post by TweFoju on 2011-09-30
thanks. so does the installation needs to be in order?

like image 1st, or header 1st?

or i can just randomly select anyone of them and just install randomly?

thanks

---

### Post by garvinrick4 on 2011-09-30
> **TweFoju said:**
> thanks. so does the installation needs to be in order?

like image 1st, or header 1st?

or i can just randomly select anyone of them and just install randomly?

thanks
Just click on each one just as I have listed in this order.
all.deb
headers
image

---

### Post by TweFoju on 2011-09-30
ok thanks ill post the update!

---

### Post by TweFoju on 2011-09-30
Works! thanks man! awesome! ;)

i hope no more crashing!!

anyway, after doing this, i dont happen to have 2 kernels right?

does this replace the 38-11? or i still have the 38-11 as a backup in case this one fail or something?

:D

anyway, after the kernel update

my laptop fan started to kick like crazy and soo loud! . and then it will stop for a while, then start again, then stop again..

err. is this the issue?

---

### Post by garvinrick4 on 2011-09-30
> does this replace the 38-11? or i still have the 38-11 as a backup in case this one fail or something? No you have both of them, if you hold shift down while
it boots you will see the menuentry screen in which to choose which kernel as to boot.
It will take the latest kernel out as default unless you change, but that is another story.
##Kernels will not be removed unless you remove it like in previous post, I believe I went through. (yes post 6)
> anyway, after the kernel update
my laptop fan started to kick like crazy and soo loud! . and then it will stop for a while, then start again, then stop again..
err. is this the issue?      Does not seem like a kernel issue, fan going nuts on you.

> err. is this the issue? What issue?

---

### Post by TweFoju on 2011-09-30
im going to try Kernel 3.0

the fan is going nuts on 39 >.<

---

### Post by garvinrick4 on 2011-09-30
first I gave you module-init-tools link to download the .deb file in one of my posts.
install that same way. (post 8 I see now) it will go straight to page and in lower left has the 64 bit .deb package to download.

---

### Post by TweFoju on 2011-09-30
Yup got it. thank you. just a question. these kernel is not official right? But its newer than official kernel right?

ohh wait

you mean if i am going to use Kernel 3.0, then i better download the init tools and install them 1st before i install the Kernel 3.0?

---

### Post by garvinrick4 on 2011-09-30
> **TweFoju said:**
> Yup got it. thank you. just a question. these kernel is not official right? But its newer than official kernel right?
No its a official real kernel, I have to use the 3.0 and up in Natty because my Network
wifi card and driver work better with 'iwlagn" Intel. 
Just get a good kernel and go with it. You will
still get updated kernels on your regular upgrades but the 3.0 kernel will still boot as
first in order. Just remove kernels if you get to many installed. If you only have one
install not a big deal will not even notice with grub 1.99 that Natty uses now. 
Happy you got your machine up and running in a fashion you are satisfied with.
Please mark as Solved in upper right under Thread Tools so others with same can
benefit from your Thread. Take care Twefoju, hope to see you hanging around these
Forums.
> ohh wait
you mean if i am going to use Kernel 3.0, then i better download the  init tools and install them 1st before i install the Kernel 3.0? 		                   		  		  		  		  		 		 			 				
Thought you were already running until you edited your post. Yes if 3.0 kernel upgrade the module-init-tools I gave you.

---

### Post by TweFoju on 2011-09-30
hey 1 more question there

i edited my post =P

dont worry, i just did a clean install on my uBuntu a while ago after the Kernel 39

now im going for the 3.0 staight from 38-11

so yeah, that question, did you mean i should install the init tools if im going for 3.0?

or i can just do the same thing as in 39

( which is to download the 3 files and download them through the download center? )

---

### Post by garvinrick4 on 2011-09-30
> did you mean i should install the init tools if im going for 3.0?
Yes.

---

### Post by TweFoju on 2011-10-01
the kernel i downloaded is 3.0.0

is that fine by using the init tool which is 3.13?

---

### Post by garvinrick4 on 2011-10-01
> is that fine by using the init tool which is 3.13
Yes it is. Are you done?

---

### Post by TweFoju on 2011-10-01
just finished installing init tools

now installing the packages 

give me 10 min haha

anyway that init tools is just the files right, i do not install the kernel 3.0 through the init tools?

so after i install init tools, now install the rest using the same way which is throuhg the software center right?

sorry for noob question haha

---

### Post by garvinrick4 on 2011-10-01
> so after i install init tools, now install the rest using the same way which is throuhg the software center right? Yep you got it.

---

### Post by TweFoju on 2011-10-01
my software center hang while installing the image

im still waiting for it to response, but yeah, i will see if 3.0 still make my fan go nuts or not ( hopefully not )

and hope it stops the crashing, cmon 3.0! u are my only hope!

thanks for the help man, i appreciate it so much!

i will mark this as solved 

):P

---

### Post by garvinrick4 on 2011-10-01
Let me know if the image installed sometimes we have to do it from the command line.
Drop the image .deb file on the Desktop.
```
cd Desktop
``````
ls
``````
sudo dpkg -i copy and paste the package name from ls here 
``` Will install now.

---

### Post by TweFoju on 2011-10-01
^
^

can this be used to install the packages?

because the software center isn't responding until now

i dont know why

but do you know a command line i can use to install the package instead of opening the package using the software center?

---

### Post by TweFoju on 2011-10-01
hey garvinrick,

i reinstall the header

but then it failed and says "nvidia-current failed to install"

but the software manager still reads it as complete ( now i can do reinstall on the button )

you know why?

--- update ---

using kernel 3.0 now, so far no problem

the only problem was

during the image and kernel install

the Nvidia-Current failed to install

which cause an report error message, and i reported it anyway

but both package still install

should i do something about the nvidia-current being left out from the installation?

---

### Post by garvinrick4 on 2011-10-01
Is the kernel installed? I have no idea where you are now.
Did you install all 3 .debs and the module-init-tools that is 4 items?
Why are you reinstalling things?
Do you need nvidia-current if you do we can install it?
Did you reboot?
```
grep menuentry /boot/grub/grub.cfg
```

All we want to do is install 4 .deb packages and reboot.

---

### Post by TweFoju on 2011-10-01
Yes Kernel is installed

all went smooth ( well, not technically )

4 files installed

BUT

the image and header

while installing it

during the end, both of them have error message because the Nvidia-current failed to install

i dont know why they want to install Nvidia-current

but. in the end, they both successfully installed ( because the button changed to uninstall )

but again, 

i dont know if they fully installed due to the nvidia thing getting error during their installation ( like maybe there is some files missing? )

your thought?

oh and what is that command you are giving me?

so my system monitor now showing me using 3.0

so far, fans are normal, no more crashes like in 38-11

---

### Post by garvinrick4 on 2011-10-01
nvidia-current is a package if you do not nvidia card no big deal sounds as if 
you are doing fine. I do not use you see is not installed and you can read
what it is for.
If you ever needed it installed the same as any other package in repositorys
sudo apt-get install nvidia-current
```
Package: nvidia-current                  
State: not installed
Version: 270.41.06-0ubuntu1
Priority: optional
Section: restricted/misc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 152 M
Depends: x11-common (>= 1:7.0.0), make, sed (> 3.0), dkms, linux-libc-dev,
         libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6
         (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1,
         zlib1g (>= 1:1.1.4), xorg-video-abi-10, xserver-xorg-core (>=
         2:1.10.0-0ubuntu1~)
Recommends: nvidia-settings
Conflicts: nvidia-180-modaliases, nvidia-185-modaliases,
           nvidia-current-modaliases
Replaces: nvidia-180-modaliases, nvidia-185-modaliases,
          nvidia-current-modaliases
Provides: xorg-driver-video, xserver-xorg-video-10
Description: NVIDIA binary Xorg driver, kernel module and VDPAU library
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat
 panel displays are also supported. 
 
 This package also includes the source for building the kernel module required
 by the Xorg driver, and provides NVIDIA's implementation of the Video Decode
 and presentation API. The latter enables acceleration for GeForce 8 and later
 series cards for h264 video. 
 
 GPUs such as GeForce series 6 or newer are supported. 
 
 See /usr/share/doc/nvidia-current/README.txt.gz for a complete list of
 supported GPUs and PCIIDs

```
> so my system monitor now showing me using 3.0
so far, fans are normal, no more crashes like in 38-11 		                   		  		  		  		  		 		 			 				
You are done enjoy your Ubuntu.

---

### Post by TweFoju on 2011-10-01
well my laptop is using nVidia

so yeah i guess even if it has error during the installation, but it seems like it does not harm the Kernel installation, i think it's just that i havent install any nvidia driver that is why it was saying error

(hopefully it really does nothing towards the kernel install )

anyway, thanks for the nvidia but no thanks, because i think it will still not support the optimus

or should i? haha

---

### Post by TweFoju on 2011-10-01
ah i take that back

finally it crashes again, only it took longer to crash than 2.6.38-11

is this a problem with x64?

because im getting tired of the random crashes :(

---

### Post by dino99 on 2011-10-01
> **TweFoju said:**
> ah i take that back

finally it crashes again, only it took longer to crash than 2.6.38-11

is this a problem with x64?

because im getting tired of the random crashes :(

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by garvinrick4 on 2011-10-01
> because im getting tired of the random crashes
Specify what you mean by crash's do you get a error message?
Does it just freeze up?
It might be something that a user has had the same.
There are lots of different machines cards and drivers.
Start a new thread with new Title about random crashes and post these with it. Just copy and paste output of code: (Stick with it Twefoju.)
Click on my name and leave me a message with url of your new Thread.
```
lspci -k
```
and your make and model of machine.

---

### Post by TweFoju on 2011-10-01
all right, will do,

PM sent btw

---

