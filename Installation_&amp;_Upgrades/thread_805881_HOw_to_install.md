---
title: "HOw to install??"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by raedbenz on 2008-05-24
HI...
i am new to Linux world.
it seems there are a lot of ways to install an application in Ubuntu, like using:

1. Add/remove applications
2. Synaptic 

what is the pros and cons for each one?
does the first method gets the file form internet and install it??
and synaptic just searches the hard disk for installation package?? 

i also tried to double click an installation package (e.g.aMSN application), then i click the install button and it processes and complition, but i cant find the installed program. where it is????

thanks

---

### Post by Pumalite on 2008-05-24
1 and 2, they both address the Ubuntu universal repos and they are the best way to install software in Ubuntu. You can go to the Terminal and:
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install <packagename>
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ivze on 2008-05-24
Add/remove and Synaptic have much common: they use the same low-level package system. Everything that can be done via Add/remove can also be done with Synaptic. Hovewer, Add/remove is just a more convinient way of installing an application: apps have their names, symbols; if you tried to do the same with synaptic, you would have to search within numbers of similar-looking packages. Generally, Synaptic can do more, but this power is not allways necessary.
Since both Synaptic and Add/Remove use the same package manager, the installation processes are similar. A user chooses some apps/packages and clicks "Install" -> the packages are downloaded from various sources, including Internet repositories (this can be changed from Synaptic: [menu]Setup|repositories - the config also affects add/remove) -> the packages are installed.

---

### Post by Rallg on 2008-05-24
Add/Remove applications is best for new users who simply want to do exactly that: add or remove applications.

The reason is that add/remove offers you a limited choice of things that are most likely to be of interest to you. When you add something, it will also bring in the necessary support files.

Synaptic offers you a choice of all packages and support files that are available through the distribution and its related suppliers. Here you can find applications that are more exotic. You can also find specialized support files and, if you are a programmer, the files needed to create or compile programs from source code.

Some users prefer to use Synaptic when removing something, since it is easier to tell what else may be removed at the same time. Once in a while, you may find that a package is "broken" (missing something) and Synaptic can help you find the missing parts.

Keep in mind that the number of packages shown, either in add/remove or Synaptic, depends on which repositories you have enabled. If you have not enabled a repository containing (for example) restricted packages, then they won't be shown in the list.

There are also packages that are not in any repository, since they are not part of the distribution or its related suppliers. Such packages typically involve source code for experimental purposes, and they must be obtained from other locations by ordinary Internet downloads.

---

### Post by raedbenz on 2008-05-24
thanks
But do u have any idea about this issue i mentioned in the beginning?
> i also tried to double click an installation package (e.g.  aMSN.package application), then i click the install button and it processes and complition, but i cant find the installed program. where it is????

---

### Post by wpshooter on 2008-05-24
> **raedbenz said:**
> thanks
But do u have any idea about this issue i mentioned in the beginning?

If this is a Microsoft compatible application you are not going to be able to install and run it under Ubuntu UNLESS you install it thru something like WINE (which I don't recommend).

---

### Post by raedbenz on 2008-05-24
well it is not Windows application.
it is an Autopackage with the '.package' extension....
i re installed and i still cant find it.

---

### Post by Pumalite on 2008-05-24
Post the complete name of the package.

---

### Post by raedbenz on 2008-05-24
the name is:

amsn-0.97-1.tcl85.x86.package

---

### Post by pixel :-) on 2008-05-24
normally it's alredy installed, maybe you where expecting an icon on the desktop?You should find it in the submenu "internet"
If you can't find it type in a terminal "amsn".You can edit the menu and add it manually,and add it manually as an icon on the desktop.

it's also in the repositories.Prefer installing from the repositories,in general the depedencies are settled correctly.

---

### Post by raedbenz on 2008-05-24
i have just also intsalled Adobcarobat reader just by double clicking the package with ".deb" format, and started installing.
i checked the Synaptic and it says the application is installed, but i cant find it in applicationss.
where it should be???
y its doesn't appear in the applications or desktop automatically? what should be pre-configured for that?
plz help...

---

### Post by pixel :-) on 2008-05-25
Not all applications add them selves in the menus,this depends on the person that build the specific packages.Open a terminal,looks like a little TV(in system,or something similar).If you know the command try it(i never installed adobe's acrobat)

If you in deed know the correct command, you can add it manually in the menus and desktop.

Try right clicking,on the **menu** and chose to edit it,i'm in kde, so i don't remember if it really is this,if it isn't search somewhere,you should find how to edit the menu(system setting?).In the menu editor add an item the name you want and an icon,and give it the command that  you want.

For the **desktop**,you can drag and drop an item from the menus to the desktop.From scratch,right click and chose new-->link to application,(or something similar) ,chose a name and icon,in application tab,type the command.It must be very similar in gnome.

If you **don't know the command**.In synaptic, go to the package, right click,and check properties,there go to installed files.You'll see a bunch of stuff,your interested only for what is located in the **/bin directories, almost always it's in /usr/bin,thies are the executables, try them until you find the one you want

---

### Post by Pumalite on 2008-05-25
[http://www.ubuntugeek.com/top-posts](http://www.ubuntugeek.com/top-posts)

---

### Post by raedbenz on 2008-05-25
Hi ,,,is it possible to add the "Home" folder as a shortcut to the desktop??

---

### Post by Pumalite on 2008-05-25
Pickup the icon and move it to your Desktop.

---

### Post by raedbenz on 2008-05-25
> **Pumalite said:**
> Pickup the icon and move it to your Desktop.

HI i am trying to drag and move but error msg occurs.
plz have a look to screenshot.[ATTACH]71590[/ATTACH]

---

### Post by Pumalite on 2008-05-25
You might not have enough space in your hard drive.
Post:
df -h

---

### Post by raedbenz on 2008-05-25
> **Pumalite said:**
> You might not have enough space in your hard drive.
Post:
df -h

is that enough space?? [ATTACH]71595[/ATTACH]

---

### Post by Pumalite on 2008-05-25
I couldn't tell. Is home hanging from '/'? What the size of your drive and what arrangement do you have for /home? How many GB are left for /home?

---

### Post by raedbenz on 2008-05-25
> **Pumalite said:**
> I couldn't tell. Is home hanging from '/'? What the size of your drive and what arrangement do you have for /home? How many GB are left for /home?

yes "home" is hanging from "/" .
total hard drive size is 13Gb, free space available is 9Gb.

thanks

---

### Post by Pumalite on 2008-05-25
It might not be enough to move it from where it is. I have a separate /home partition and more space and I had no problems doing it.

---

### Post by soldersplash on 2008-05-25
Hi raedbenz,

I think I see your problem. I just tried this out myself and found the following.

If I browse to my home folder and try and drag it onto the desktop I get the same error message as you. 

_But_ if I go to the Places menu and drag Home Folder from there to desktop it works! :guitar:

Good luck,

---

### Post by raedbenz on 2008-05-25
> **soldersplash said:**
> Hi raedbenz,

I think I see your problem. I just tried this out myself and found the following.

If I browse to my home folder and try and drag it onto the desktop I get the same error message as you. 

_But_ if I go to the Places menu and drag Home Folder from there to desktop it works! :guitar:

Good luck,

HI ,thanks
yes it worked,,,
but it creates a copy for whole contents..what i am looking for is just a shortcut(link)...
thanks

---

### Post by soldersplash on 2008-05-25
Ooops.... Sorry. Didn't notice that straight away. :(

I have now tried the following:-
Open a terminal and " sudo ln --symbolic /home/YourName /home/YourName/Desktop/".

(Replacing YourName with whatever your home folder name actually is..) 

I am sure this doesn't duplicate the actual files :) just makes a symbolic link to the original directory. 

Cheers,
Soldersplash

---

### Post by raedbenz on 2008-05-25
> **soldersplash said:**
> Ooops.... Sorry. Didn't notice that straight away. :(

I have now tried the following:-
Open a terminal and " sudo ln --symbolic /home/YourName /home/YourName/Desktop/".

(Replacing YourName with whatever your home folder name actually is..) 

I am sure this doesn't duplicate the actual files :) just makes a symbolic link to the original directory. 

Cheers,
Soldersplash

HI ,,thats what i am getting

raed@raed-laptop:~$ sudo ln --symbolic/home/raed/home/raed/Desktop/
ln: unrecognised option `--symbolic/home/raed/home/raed/Desktop/'
Try `ln --help' for more information.
raed@raed-laptop:~$

---

### Post by raedbenz on 2008-05-25
ok i did it,,
thanks again

---

### Post by soldersplash on 2008-05-25
No probs, we're both newbies by the looks of of it and this is exactly what the forums are for. Helping each other out. I got some great advice over on another thread today about Google Earth and so it is nice that _I_ could help someone (in the end). I clicked on the 'thanks' button on the people in the thread that helped me out to show my gratitude.

Cheers and happy Linuxing!

---

