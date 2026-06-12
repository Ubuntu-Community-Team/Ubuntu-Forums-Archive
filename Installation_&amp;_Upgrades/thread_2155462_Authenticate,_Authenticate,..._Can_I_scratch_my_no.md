---
title: "Authenticate, Authenticate,... Can I scratch my nose without Authenticate ?"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by NuxNik on 2013-06-18
Hello,

Finally decided to get serious about trying to find an alternative solution to the product from Redmond. Vista, Windows 7 have helped push me in that direction
I have a small home network for the family. The only real issue is limiting some access to the kids, which I can do with the router
So security is very low priority. Particularly so, on the box that I am currently using for trying out distros
I have installed Lubuntu 13.04 (64 bit)  Only one user identified on it
I am constantly being annoyed with slightly different  pop-ups asking to authenticate for just about anything I want to do..
-  mount a drive.. - Authenticate
- check for updates.. - Authenticate
- take a peek into some directory.. - Authenticate
- Scratch my nose.. - Authent..  well not yet.. but I'm getting nervous.. :-)

This is the same kind of nonsense that annoyed the hell out of me using Windows. But at least I can eliminate it by turning off Defender
Is there ANY way, to silence this nonsense in Lubuntu. ?
Or is there some Ubuntu variant that is not this paranoid ?

Note that I have also tried  Puppy Linux, and I don't have the constant requests to "Authenticate". But Puppy has other issues, such as being way too minimalist for my needs

Thanks

---

### Post by 2F4U on 2013-06-18
As far as I know, Puppy is more like a single-user system and everything is run under the root account. Usually, Linux is implemented as multi-user system. In order to prevent normal users to do harm to the system, their accounts are non-privileged and their rights are usually restricted to their home folder.

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by NuxNik on 2013-06-18
> **ahallubuntu said:**
> Try this (bottom of the page):

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

-----------------------------------------------------------------------

Thanks for your prompt response..

This clearly is for running sudo in a terminal. 
How does this apply to doing minor and ordinary things in the GUI ?
Actions that frankly are perfectly ordinary actions for just using the OS.

I REALLY do NOT see ANY advantage with constantly having to enter a password on a private computer in a private location,on a  test machine, 
I REALLY REALLY do not need or want such a high security level.

---

### Post by SeijiSensei on 2013-06-18
Only the root user can make administrative changes, so you need to accept that fact to begin with.

You can run as the root user all the time, but if you make a mistake you can render your system unusable.  Unless you have a couple of years of experience as a Unix admin, this is not an attractive option.

Let's talk about a couple of things you mentioned.  First is [mounting devices]("https://help.ubuntu.com/community/AutomaticallyMountPartitions").  If you have drives you want to mount at boot, you should enter them into /etc/fstab.  Other types of devices like USB drives you can mount as an ordinary user, though you may be the only one who can see the device.

Updating the machine's software is a task that always requires root privileges.  Windows users cannot muck about in the registry without administrative privileges either.  The fact that ordinary Windows users could once install software on their own without admin privileges or, in earlier versions, without even a warning is the reason why there are millions of compromised machines on the Internet sending spam to every email server on earth every day.

There are few directories on the system that an ordinary user cannot look into, however they cannot make any changes to the directory's contents.  What directories are you specifically blocked from viewing without root privileges?

---

### Post by NuxNik on 2013-06-19
As stated, this is test box. 
That means that I clone my partition.
If I mess up. I clone it back

Frankly, I'm flat out annoyed, that I'm forced into terminal commands for simple tasks like moving or copying files because an horrible security setup if constantly coming up with new ways to use "permission denied" for even simple tasks like moving my OWN FILES, on a 1 user box that no one else is acessing.

So do you have a solution ?
  If not, thanks for your last input..

---

### Post by QIII on 2013-06-19
Hello!

Are you saying that you are being asked to authenticate if you are moving files within the confines of your home directory?

---

### Post by SeijiSensei on 2013-06-19
> **QIII said:**
> Hello!

Are you saying that you are being asked to authenticate if you are moving files within the confines of your home directory?

That was essentially the question I asked.

As a ordinary user, you can only write to /home/username and to /tmp.  Everywhere else requires root privileges unless you change the permissions on the appropriate directories accordingly.

As I said, if you want to write anything anywhere, then become the root user.

---

### Post by NuxNik on 2013-06-21
> **QIII said:**
> 
Are you saying that you are being asked to authenticate if you are moving files within the confines of your home directory?



I'm not sure, but it appears so.
For example I have a memory stick that is my repository of just about everything I want to keep, including ISOs.
I was trying to copy some downloaded  ISOs from ~/>me</Downloads to media/>me</[memory stick}/xx/ISOs.
Frankly, since I'm the only user & Administrator on this box, being required to Authenticate is redundant
What's the point of a GUI if it constantly tells you're not authorized, and forces you to do everything manually in a terminal

I like GUI..Having worked decades in non-gui environments, they're the best thing since sliced bread, cell phones, shrinking electronics, >place your favorite recent improvement here<.
The're supposed to make your life easier and not force limits on you
These kind of limitations kill the benefit of the GUI.

I've run lots of stuff from "consoles"
Been there, done that, don't 'want to go back there.

---

### Post by QIII on 2013-06-21
Try this in your GUI:

Create a text file in your home directory.  Create a new folder in home.  Try to move the text file to the new folder.

If any of those operations fails, let us know.

---

### Post by NuxNik on 2013-06-24
> **QIII said:**
> 
  Try this in your GUI:
  Create a text file in your home directory.  Create a new folder in home.  Try to move the text file to the new folder.
  If any of those operations fails, let us know.



Why ?
    I have no problems puttering with files and directories in "home"
   That never was not the issue.

The issue is accessing other directories and being forced into terminal mode to do stuff that should be doable on a GUI, were the security system not set up to be so xxxx- retentive.

---

### Post by Thee on 2013-06-24
That's really not suppose to happen. You should be able to move files from and to your home directory, to USB drives, Windows partitions, etc. As long as its not to folders which belong to root.

---

### Post by QIII on 2013-06-24
> 
Why ?
    I have no problems puttering with files and directories in "home"
   That never was not the issue.

This indicates that  things are working properly.  You own what is in your home, and root  owns what is in system directories.  You need to have elevated  privileges to modify those directories and their content.  You have to do the same to modify what is in another user's home directory.

The  same applies to every distro I use, as well as my Windows 7  installation.  You are not being kept from modifying your own system, it  is simply necessary to elevate your privileges as necessary -- a trait  common to Linux distributions where you don't, by default, log in as  root.

I appreciate your frustration and recognize that you have every right to be unhappy about this.  

I'm  not an Ubuntu evangelist, so I have no problem in suggesting that if  this arrangement does not work for you, you have the option to go to a  different distro.  There is absolutely nothing wrong with that and  nobody here should give you any grief for that.

It doesn't make any sense to me to persist in using something that is not working for you.  It is not worth the effect on your blood pressure.

---

### Post by NuxNik on 2013-06-28
> **2F4U said:**
> 
As far as I know, Puppy is more like a single-user system ,,, <snip>.... Usually, Linux is implemented as multi-user system.
.

Your post made me realize that in part that is my complaint
I suspect that most Linux installations are in fact single-user systems sittng at home or even in an office.

As such the whole superstructure of that is valid for a multi-user system is quite redundant in such cases.
There is also the complete nonsense about being repeatedly asked to ID yourself, or having to to go through useless extra steps because of it.

Apparently, no on has yet really taken time to spend some clear thought on the subject.

---

### Post by buzzingrobot on 2013-06-28
While I sympathize with the OP, I'm not aware of any Linux that will allow an ordinary user to copy fies into a root-owned directory. That kind of permission system has been around in Unix since the beginning. changing it would likely percolate out all kinds of issues.

If I had something like /media/me and I wanted to put files there as an ordinary user, I'd change ownership of "me" from root to "me".


Also, something like "gksudo nautilus" via alt-f2 gets you a file manager running with escalated privileges.

---

### Post by snowpine on 2013-06-28
Fortunately for the rest of us, Ubuntu is not designed by idiots. :)
I work as a Windows admin, and I get the identical behavior in Windows 7. If your Windows does not ask you for a password when performing admin tasks, it has not been correctly configured.

---

### Post by NuxNik on 2013-07-07
> **snowpine said:**
> Fortunately for the rest of us, Ubuntu is not designed by idiots. :)
I work as a Windows admin, and I get the identical behavior in Windows 7. If your Windows does not ask you for a password when performing admin tasks, it has not been correctly configured.


A most valid point when you are in a multi-user environment with graduated levels of security.
But seems a bit redundant when you are the sole user/administrator and chief bottle washer on a box that is sitting alone in your SOHO.

And frankly my dog is far  too busy climbing up into trees to bother hacking it when I'm not there,

---

### Post by buzzingrobot on 2013-07-07
Yeah, we do need a better way to authenticate. 

Permissions and ownership are deeply embedded in operating systems, and passwords are part of that.

Meanwhile, visitors, relatives, repair people, etc., all have physical access to computers that are otherwise used by one person.

---

### Post by Frogs Hair on 2013-07-07
Due to the circular nature of this discussion and since password authentication is a currently  supported feature of Ubuntu/Linux the thread is closed.

---

