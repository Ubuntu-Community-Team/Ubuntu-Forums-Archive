---
title: "Can't install Brother DCP-195c printer on 11.04"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by sophy_m on 2011-05-12
I have a Brother DCP-195c printer/scanner, which after a bit of wrangling worked fine on 10.10. Since installing 11.04 (upgrade didn't work so had to start fresh) I can't get to do anything! I've followed all the instructions on the Brother site (which worked for 10.10), and several how-tos elsewhere (for previous distros, admittedly), and still it just says can't find driver. When I open the printer app, it knows it's there, but it doesn't have the correct model in the driver list.

Anyone in possession of the secret to getting it working?!

---

### Post by Matt__ on 2011-05-12
there is a driver from the [Brother Solutions Center](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html). (I assume this is the one you tried)
Its only listed up to 9.04 but hopefully will work for you. Sadly your model isnt list on the [Openprinting](http://www.openprinting.org/printers) list but perhaps you can find another driver that works.

Is there any reason why you upgraded to 11.04 if everything was working in 10.10?

there is also this terminal command I found on [Launchpad](https://answers.launchpad.net/ubuntu/+source/simple-scan/+question/141184) (again its for 10.10)
```
cd ~; wget http://www.brother.com/pub/bsc/linux/dlf/dcp195clpr-1.1.2-1.i386.deb; sudo dpkg -i ./dcp195clpr-1.1.2-1.i386.deb; rm ./dcp195clpr-1.1.2-1.i386.deb; wget http://www.brother.com/pub/bsc/linux/dlf/dcp195ccupswrapper-1.1.2-2.i386.deb; sudo dpkg -i ./dcp195ccupswrapper-1.1.2-2.i386.deb; rm ./dcp195ccupswrapper-1.1.2-2.i386.deb; sudo apt-get -f install
``` copy and paste as one command.

---

### Post by sophy_m on 2011-05-12
Thanks! That command *almost* got it working. It now recognises the printer as working and sends jobs to it - but they aren't getting through to the machine for some reason! Maybe something's pointing to the wrong place.

If I never upgraded because everything was working fine, I'd still be using Gutsy... Plus it's fun to press buttons.

---

### Post by Billxyzzy on 2011-05-12
Your problem is not unique see my bug report launchpad 
#769241. I have a DCP-7040 and it has the same problem.
I got the scanner function working by downloading the
latest scanner drivers from Brother.  However, the 
printer drivers are very much out of date.
So far there has been no activity on the bug report.
I have been trying to get brother to provide updated
drivers but so far no luck. Please add your me-too to the
bug report.  I have put a lot of time into this.
Further,  this problem exists with the latest openSUSE
and Debian.  It is not just a Ubuntu problem.

---

### Post by sophy_m on 2011-05-13
> **Billxyzzy said:**
> Your problem is not unique see my bug report launchpad 
#769241. I have a DCP-7040 and it has the same problem.
I got the scanner function working by downloading the
latest scanner drivers from Brother.  However, the 
printer drivers are very much out of date.
So far there has been no activity on the bug report.
I have been trying to get brother to provide updated
drivers but so far no luck. Please add your me-too to the
bug report.  I have put a lot of time into this.
Further,  this problem exists with the latest openSUSE
and Debian.  It is not just a Ubuntu problem.

Thanks, I have managed to get it working now - I'm not quite sure how, though! Something to do with CUPS I think. I modified something in CUPS (which worked after I used the command given by Matt) and it magically started working...

---

### Post by Billxyzzy on 2011-05-13
Would you mind telling me just what you modified in CUPS?
What command?  Are you using i386 (32bit) or amd64 (64bit)
In 64bit all installs fail

---

### Post by walt.smith1960 on 2011-05-13
> **Billxyzzy said:**
> Would you mind telling me just what you modified in CUPS?
What command?  Are you using i386 (32bit) or amd64 (64bit)
In 64bit all installs fail

Are you using the command line install for 64 bit? Brother drivers are 32 bit so you have to use the -force switch in dpkg in order to get it to install.

---

### Post by Billxyzzy on 2011-05-13
I am using the command line.
Here is the output
sudo dpkg -i --force-depends /home/bill/Downloads/brdcp7040lpr-2.0.2-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 410750 files and directories currently installed.)
Preparing to replace brdcp7040lpr:i386 2.0.2-1 (using .../brdcp7040lpr-2.0.2-1.i386.deb) ...
Unpacking replacement brdcp7040lpr:i386 ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing /home/bill/Downloads/brdcp7040lpr-2.0.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /home/bill/Downloads/brdcp7040lpr-2.0.2-1.i386.deb
I have been fighting this problem for about 2 weeks now.
See the launchpad bug listed above.

---

### Post by walt.smith1960 on 2011-05-13
> **Billxyzzy said:**
> I am using the command line.
Here is the output
sudo dpkg -i --force-depends /home/bill/Downloads/brdcp7040lpr-2.0.2-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 410750 files and directories currently installed.)
Preparing to replace brdcp7040lpr:i386 2.0.2-1 (using .../brdcp7040lpr-2.0.2-1.i386.deb) ...
Unpacking replacement brdcp7040lpr:i386 ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing /home/bill/Downloads/brdcp7040lpr-2.0.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /home/bill/Downloads/brdcp7040lpr-2.0.2-1.i386.deb
I have been fighting this problem for about 2 weeks now.
See the launchpad bug listed above.

I'm in no way knowledgeable in bash or the command line, more of a 'monkey see-monkey do" kind of noob.  What does the "--force-depends" do?  I just used "--force", not "--force-depends".  What happens if you leave "depends" off?

---

### Post by Billxyzzy on 2011-05-13
There are options with the --force,  --force all
--force depends is similar to force all and overrides
any settings for example
Edit:
package architecture (i386) does not match system (amd64)
This is the key problem,  all of the printer drivers
are i386 and will not be accepted on the natty
implementation of the system.
This is a deadlock and a catch 22 situation.
Without brother providing 64 bit drivers I am stuck

---

### Post by walt.smith1960 on 2011-05-13
> **Billxyzzy said:**
> There are options with the --force,  --force all
--force depends is similar to force all and overrides
any settings for example
Edit:
package architecture (i386) does not match system (amd64)
This is the key problem,  all of the printer drivers
are i386 and will not be accepted on the natty
implementation of the system.
This is a deadlock and a catch 22 situation.
Without brother providing 64 bit drivers I am stuck

I'm not knowledgeable enough to be of much help but I have a Brother MFC-6490CW installed on an AMD64 system. Print and scan no problem.  I just followed the directions on the Brother site, wish I knew how to help you.  The other thought I had is to send a support request.  There is email only support available from Brother in Japan.  Not real fast but if you're out of other options..............

Here's the link I have:  [https://secure6.brother.co.jp/LinuxContactUs/contact/Linuxform.html](https://secure6.brother.co.jp/LinuxContactUs/contact/Linuxform.html)

---

### Post by Billxyzzy on 2011-05-13
I looked up the specs for the MFC-6490.
It is interesting that the drivers are dated 2008 much like
the drivers for my printer. However,  there is one big
difference,  you have inkjet and I have a laser printer.
Yours is color and mine is monochrome.  It is a printer,
scanner, copier.  No fax function. I will go back and look
at the other specs and see if is on the compatibility
list.  Not all are on the list and it seems to be hit
and miss.

---

### Post by Billxyzzy on 2011-05-13
I looked up the specs for the MFC-6490.
It is interesting that the drivers are dated 2008 much like
the drivers for my printer. However,  there is one big
difference,  you have inkjet and I have a laser printer.
Yours is color and mine is monochrome.  It is a printer,
scanner, copier.  No fax function. I will go back and look
at the other specs and see if is on the compatibility
list.  Not all are on the list and it seems to be hit
and miss.

Edit,  I have already sent e-mails to them and not gotten
a reply so far.  I was under the impression that the contacts were here in the US.

---

### Post by walt.smith1960 on 2011-05-14
> **Billxyzzy said:**
> I looked up the specs for the MFC-6490.
It is interesting that the drivers are dated 2008 much like
the drivers for my printer. However,  there is one big
difference,  you have inkjet and I have a laser printer.
Yours is color and mine is monochrome.  It is a printer,
scanner, copier.  No fax function. I will go back and look
at the other specs and see if is on the compatibility
list.  Not all are on the list and it seems to be hit
and miss.

Edit,  I have already sent e-mails to them and not gotten
a reply so far.  I was under the impression that the contacts were here in the US.

They do have U.S. based phone support but for Windows and Mac only. Linux support is email only.

---

### Post by sophy_m on 2011-05-14
> **Billxyzzy said:**
> Would you mind telling me just what you modified in CUPS?
What command?  Are you using i386 (32bit) or amd64 (64bit)
In 64bit all installs fail

I think it had printer location set to something generic, so I selected my printer from the list of local printers. I'm on i386.

This is the terminal command I used.
```
cd ~; wget http://www.brother.com/pub/bsc/linux/dlf/dcp195clpr-1.1.2-1.i386.deb; sudo dpkg -i ./dcp195clpr-1.1.2-1.i386.deb; rm ./dcp195clpr-1.1.2-1.i386.deb; wget http://www.brother.com/pub/bsc/linux/dlf/dcp195ccupswrapper-1.1.2-2.i386.deb; sudo dpkg -i ./dcp195ccupswrapper-1.1.2-2.i386.deb; rm ./dcp195ccupswrapper-1.1.2-2.i386.deb; sudo apt-get -f install
```

---

### Post by mörgæs on 2011-05-14
I had a similar (I guess) problem with a DCP-130C. The driver installed fine from Synaptic, but this screen
[http://imageshack.us/photo/my-images/35/brother130.png/](http://imageshack.us/photo/my-images/35/brother130.png/)
showed that the wrong driver was used. 

Changing driver in the system -> administration -> print - menu solved the problem.

---

### Post by Billxyzzy on 2011-05-14
@soph_m " I'm on i386." That is the whole point I have been
trying to make.  I386 will work but amd64 will not.
Drivers for one will not work on the other.

The other problem is that if your device is not on the
list then there are no drivers available in synaptic or
on the printer device list to choose from.
I have spent far too much time with this and the devs
do not think my bug report is important.

I am looking at other distro's and will see if I can
solve the problem.  For me Ubuntu has reached EOL and
does not seem to be going the way I need.
I need a system that will work with my hardware not
spend my time on long searches for a bandaid solution.

---

### Post by Anna Lee Fdez on 2011-05-24
I have just purchased a Brother DCP-195c printer.  It passed its print test but when I insert the disk to install it tells me my "Operative System is not compatible.  Check the requirements for the system for the model and install an adequate OS version". I have Windows XP and the disk says Windows 7.  I'm certainly not very good at fixing anything like this. What can I do?? anna

---

### Post by mörgæs on 2011-05-25
Are you aware that this is a forum for Ubuntu and not for Windows? I don't think many people in here can help with this kind of problems.

Anyway, support for XP is running out next year, and then you have to install something different on the machine. Have you thought about trying Ubuntu? As you can see above, it is possible to get a 130C to work, so it should also be with a 195.

---

