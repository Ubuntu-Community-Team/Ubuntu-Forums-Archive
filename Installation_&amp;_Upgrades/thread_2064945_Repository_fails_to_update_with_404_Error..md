---
title: "Repository fails to update with 404 Error."
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by Paul Lynch on 2012-09-30
Similar problem here. I final decided to make the jump and upgrade from 10.4 to 12.4 and I get a load of errors when I use the update manager, ......

                                  W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources)  404  Not Found [IP: 91.189.92.184 80] 
 , W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources)  404  Not Found [IP: 91.189.92.184 80] 
 , W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.184 80] 
 , W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources)  404  Not Found [IP: 91.189.92.184 80] 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/main/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/restricted/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/universe/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/main/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/main/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/main/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/universe/binary-i386/Packages)  404  Not Found 
 , W:Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  404  Not Found 
 , E:Some index files failed to download. They have been ignored, or old ones used instead.
  

Looks like a lot of fundamental packages are unavailable, can some one assist, I don't want to change my sources list without some concrete advice

Thanks in advance.

---

### Post by jerrrys on 2012-09-30
Hi Paul.  First off you really should of started your own thread, [s]maybe a mod will come along and split this up.[/s] - a mod has!

Anyhow your sources.list are a bit of a mess.  Try this in terminal:

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old

sudo apt-get update

Did that do any good?  If not, please post the output of:

cat -n /etc/apt/sources.list

---

### Post by sffvba[e0rt on 2012-09-30
*Posts moved to **new** thread.*


404

---

### Post by sandyd on 2012-09-30
**Thread split into own thread.**

^^ hi not_found, multi-modding eh? :P

---

### Post by Paul Lynch on 2012-10-02
Jerrys,

thanks for the assistance so far. I followed your direction (I should have figured out the sources list update had I of spent more time searching this forum). The sources update has progressed me to the next hurdle, now when I run the update manager I get the following text and the UM fails...

[I]
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list - ifstream::ifstream (13: Permission denied), E:The list of sources could not be read.'[/I]

When I run cat -n /etc/apt/sources.list     in the terminal i get a permission denied, which is puzzling me, I have full admin rights on my machine and never had this issue before.

[I]paul@paul-desktop:~$ cat -n /etc/apt/sources.list 
cat: /etc/apt/sources.list: Permission denied
paul@paul-desktop:~$ [/I]

Appreciate if you can help out as I am a pure nub. Probably wont get a chance to wouk on this till the weekend but if you leave a post I will pick it up ... eventual.

---

### Post by Paul Lynch on 2012-10-03
Bump

---

### Post by jerrrys on 2012-10-03
Wasn't expecting to hear from you till the weekend :)

Lets try a different approach.  Open a terminal and enter:

gksudo nautilus

Then go to your filesystem and navigate to /etc/apt/sources.list

And be careful what you do, sudo can be very unforgiving.

---

### Post by Paul Lynch on 2012-10-05
Ok so I followed your direction and opened the sources.list file which opens the Software Sources window, everything in here looks normal, what should I be looking for?

---

### Post by Paul Lynch on 2012-10-05
One thing of note, all the options in the Software Sources window are unselected in each tab.

---

### Post by jerrrys on 2012-10-05
> **Paul Lynch said:**
> Ok so I followed your direction and opened the sources.list file which opens the Software Sources window, everything in here looks normal, what should I be looking for?

That "cat -n" command should of done the same thing.  Anyhow would you go ahead and post that (copy and paste).

---

### Post by jerrrys on 2012-10-05
> **Paul Lynch said:**
> One thing of note, all the options in the Software Sources window are unselected in each tab.

Take a screenshot of that and post it please.

---

### Post by Paul Lynch on 2012-10-12
So the screen below is where I am on this, all looks normal in the sources list to me.

---

### Post by Paul Lynch on 2012-10-12
screen

---

### Post by Paul Lynch on 2012-10-13
Bump

---

### Post by oldos2er on 2012-10-13
I usually tick all the boxes. If you tick all the boxes, and have the main server enabled (as in your screenshot), do you see any errors when you run ```
sudo apt-get update && sudo apt-get upgrade
``` ?

---

### Post by Paul Lynch on 2012-10-13
So I did that and the following updated
[I]
paul@paul-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IE
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IE
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IE
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IE
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paul@paul-desktop:~$ [/I]

Still when I run Update Manager I get the error
[I]
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list - ifstream::ifstream (13: Permission denied), E:The list of sources could not be read.'
[/I]

---

### Post by oldos2er on 2012-10-13
Can you post the output from ```
groups
``` ?

---

### Post by Paul Lynch on 2012-10-14
[I]paul@paul-desktop:~$ groups
paul adm dialout cdrom plugdev lpadmin admin sambashare
paul@paul-desktop:~$ [/I]

Looks like I have admin rights but no permission as above.... HELP

---

### Post by oldos2er on 2012-10-14
Looks like your user is missing the 'sudo' group. Are there other users on this system that have sudo privileges?

---

### Post by Paul Lynch on 2012-10-14
No just me

---

### Post by oldos2er on 2012-10-14
You may need to boot into recovery mode to add your user to the sudo group ```
adduser paul sudo
```

---

### Post by Paul Lynch on 2012-10-15
Hi I'm having some difficulty booting into recovery mode, I press escape when after the BIOS loads but the machine continues on to the main login page. Do you have another suggestion?

---

### Post by wojox on 2012-10-15
> **Paul Lynch said:**
> Hi I'm having some difficulty booting into recovery mode, I press escape when after the BIOS loads but the machine continues on to the main login page. Do you have another suggestion?

Hold down the left Shift key.

---

### Post by Paul Lynch on 2012-10-15
OK so that was progress, I booted into recovery mode added the sudo group to my profile and ran apt get update as follows

[I]paul@paul-desktop:~$ sudo apt-get update
[sudo] password for paul: 
Sorry, try again.
[sudo] password for paul: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IE
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IE
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IE
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IE
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Reading package lists... Done
paul@paul-desktop:~$ 
[/I]
I am still faced with the original problem when I run the update manager I get:

[I]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list - ifstream::ifstream (13: Permission denied), E:The list of sources could not be read.'[/I]

Any suggestions welcome...

---

### Post by oldos2er on 2012-10-15
Hmm. Maybe try the suggestion given [here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/258909")
I don't know what more to suggest.

---

### Post by jerrrys on 2012-10-15
Like oldos2er said, or just rename and update:

sudo mv sources.list sources.list.old

and update

---

### Post by Paul Lynch on 2012-10-16
Well that seems to work a treat, I removed the Sources list file and am currently updating. I guess I manually added some updates into the repo with errors. Anyhow once these updates are complete I plan on updating the system to the new LTR... fingers crossed

Appreciate all the help and effort

---

### Post by RobertEr on 2012-12-14
I have the same message basically and yes my internet is working fine and I have two other computers which are updating just fine. The big difference in my laptop is I went from Ubuntu 11.10 to Ubuntu 12.04. Would that make  a difference? I was considering overwriting with a copy  I have of Ubuntu 12.04. Please help. My laptop says my package hasn't been updated in 19 days now

---

