---
title: "Installing TB 2.0 and am I insane?"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by destined on 2007-05-27
Thought i'd pass these instructions along and see if I am all wet about TB being so easy to install..

1) Open a konsole Window.. 
2) sudo apt-get install alien (if you have alien all ready installed skip this instruction.)
3) Download Thunderbird 2.0 from main mozilla website.. Save in Desktop or your preferred directory..

4) change directory to where Thunderbird 2.0*.tar.gz is located.. (I like it in /home/username/Desktop..) So "cd /home/username/Desktop" or where ever you saved it..

5) Most important part: in konsole type:

"sudo alien -d t*.tar.gz" 

6) Step #5 may take a minute to do its job.. But after it's done, use what ever method one regularly uses to install debian files.. (you can use dpkg -i, aptitude install , or apt-get install..)

 I installed this program in Kubuntu 7.04 "Fiesty" Can some one confirm for me this works in the regular Ubuntu?

Am I all wet this is this easy to install?
destined

---

### Post by zero-Q on 2007-06-01
I tried ur way and I can say that that is nearly perfect. I had only a problem intall process with thunderbird-locale-tr and after it uninstalled there is no problem...(I am an edgy user)
thx, and best regards...

---

### Post by aysiu on 2007-06-01
What does *alien* have to do with anything? The Thunderbird from the main site isn't an .rpm file, is it?

Why don't you use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird) instead?

---

### Post by nu2this on 2007-06-01
Aysiu, your right it's a tarball a .tar.gz no less! 
Destined you can install in 3 much easier ways
1. Ubuntu Synaptic ;  Administration>Synaptic then click search type mozilla thunderbird in the box it''ll sow in the display mark it for install hit enter ,done!
2. Applications> Add/Remove
3. install Automatix from [http://www.getautomatix.com/](http://www.getautomatix.com/) 
then find & install form there.
Yes you are soaking wet! Do one of those get dry before you catch a cold;)

---

### Post by destined on 2007-06-03
[QUOTE=nu2this;2759790]Aysiu, your right it's a tarball a .tar.gz no less! 
Destined you can install in 3 much easier ways
1. Ubuntu Synaptic ;  Administration>Synaptic then click search type mozilla thunderbird in the box it''ll sow in the display mark it for install hit enter ,done!
2. Applications> Add/Remove
3. install Automatix from [http://www.getautomatix.com/](http://www.getautomatix.com/) 
then find & install form there.

As should be noted if you search the forums, Thunderbird 2.0 will not install in Kubuntu or ubuntu with a lot of help from a script. (You can find the script by searching around the forums.>) 

Became very frustrated frustrated with using the Thunderbird install script from the psy* something.. (not sure of the name) on both Kubuntu 6.10 and 7.04 (full installs not beta..) 
It kept giving me dependency errors and a lot of other things, so I wondered, could there be an easier way?

Especially since the above install ideas are a lot harder than these couple steps I am going to amend to my starting comments about how to from source from the mozilla site..

1) "sudo apt-get install build-essential alien" (in konsole or what ever flavor of ubuntu shell commander you have..)  Your going to need to get both alien AND  build-essential, so you can compile the during the alien steps..

2) Download Thunderbird 2.0 from the mozilla site..

3)  Change into directory where the thunderbird 2.0 tarball is.. mine was on the Desktop, so "cd Desktop"

4) Now go back into your favorite konsole or shell commander and type "sudo alien -d name of thunderbird source tarball here.."

Now step #3 for some reason does a double duty idea.. Alien some how CONVERTS the tarball and compiles the file into a debian package ready for install.. (now sure how it does it but maybe someone else could tell me?)

5) With your favorite package manager "aptitude, apt-get, synaptic, or adept" install the debian thunderbird file.. Fastest way imo is "sudo apt-get install name of thunderbird debian package.." Now every thing should be installed..

---

### Post by destined on 2007-06-03
Just wanted to add a warning about the "alien -d" step.. This step may take some time, as it is compiling the tarball and coverting over into a debian installer file..
Destined

---

### Post by destined on 2007-06-03
[QUOTE=nu2this;2759790]Aysiu, your right it's a tarball a .tar.gz no less! 
Destined you can install in 3 much easier ways
1. Ubuntu Synaptic ;  Administration>Synaptic then click search type mozilla thunderbird in the box it''ll sow in the display mark it for install hit enter ,done!

Is this the version thunderbird 1.5.9? or 2.0. The reason i have to move to 2.0 is the webmail additions have moved to 2.0 and won't install on the 1.5.9 or .10 (running Kubuntu 7.04)

2. Applications> Add/Remove  Either synaptic or adept based.. See my comment about thunderbird 2.0 not being in the ubuntu package archive, so synaptic and adept would be useless for my situation..

3. install Automatix from [http://www.getautomatix.com/](http://www.getautomatix.com/) 
then find & install form there.

From previous comment in other threads, automatix would have the same problem as the other two comments.. But for other reasons, I might be interested in picking this up.

Destined

---

