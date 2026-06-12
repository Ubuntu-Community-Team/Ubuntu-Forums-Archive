---
title: "[SOLVED] Server Install"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by dstein on 2006-06-12
This is my first post. I have used numerous versions of linux over the years but they have all had graphical installations, and I have always switched back to Windows. I recently decided to give Linux another shot, this time attempting to learn a lot about it.

I have decided to use Ubuntu. I am not sure why, but I thought that the Desktop version only included a LiveCD and could not be installed to the desktop. I then installed the Server version, and was surprised that the X Window System and Gnome did not load when I booted my system. After doing some research, I realized that I could have just installed the Desktop edition. Instead of doing this, I am going to try to make this a learning experience. From doing some research, I realize that I can type "apt-get install ubuntu-desktop", and a bunch of packages would be installed, including a GUI, which I can access with startx, or setup gdm and boot into a Gnome.

I am trying to learn as much as I possibly can. I would prefer to install all packages individually instead of using ubuntu-desktop, but I am not sure where I can get help with this. I have used Windows for years and I am not familiar with how "apt-get" works. How does it know where to refer to the programs I try to install? If anyone can help me out by sending suggestions on where I can learn the most, including installing the X Window System and GUI, one package at a time, I would be very greatful.

I would also like to become very familiar with the shell. This is why I chose not to start over with the Desktop CD, and why I am not going to have my system boot directly to the GUI. Please let me know if you know of any sites that list and explain a bunch of useful/important commands. and a site that explains package management thoroughly.

Thanks a lot for the help. I have been using Windows for years but I would like to finally make the switch. Thanks again.

---

### Post by dstein on 2006-06-12
After re-reading my post, I realized that I sound like I'm 3 years old. Pleae ignore my typos and spelling mistakes (ie grateful spelled greatful). Although I have not had much experience with Linux, I have had experice building computers, programming, and a little bit of networking, so replys do not need to be dumbed down, although my original post would suggest otherwise. Thanks.

---

### Post by rcarring on 2006-06-12
If you have the server install, do this:

a) sudo apt-get update
flushes and refreshes the repositories
b) sudo apt-get install mc
gives you a file manager that is easy to use etc
c) sudo apt-get install lynx
and for web browsing though its a bit shit at anything other than pure text pages

next get the xfce desktop

finally from within the xfce (xubuntu) desktop, run synaptic and get ubuntu-desktop

I would seriously recommend you do the synpatic ubuntu-desktop method because picking packages one by one is going to take a while, what with dependency issues and also that there are 364 packages to be installed, tho oddly only 63mb to download.

---

### Post by confused57 on 2006-06-12
Check out aysiu's website:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Look at the index on the left "Playing Around", it has a description of the meta-packages for (k)(x)ubuntu-desktops.

---

### Post by dstein on 2006-06-12
Thanks for the quick replies. I will try these ideas and take a look at the link. Here are some basic questions, but I should probably ask before getting started. If I install mc, can I access this program by just typing mc at the command prompt (I am not sure what it's called in Linux)? Cause in Windows/DOS, I would either have to go to the executable programs folder or add the folder to the "Path" variable. If I can run it like this, can someone explain what's going on? Is the directory where it's installed added to some sort of list or file when running apt-get? Thanks for the help. Any other advice or suggestions would be appreciated. Thanks again.

---

### Post by dstein on 2006-06-12
Another quick question I forgot to ask:

After I install ubuntu-desktop, will my machine be the same as if I installed the Desktop version rather than the Server or will there still be differences? Also, is there any type of security (virus, spyware) software I should install? Thanks.

---

### Post by mayostard on 2006-06-12
Hi,

I had the same issue.  I didn't realize you could just install ubuntu-desktop.  I happened to have another machine with the desktop distribution on it, so I just did an apt-show-versions on both nodes, then seded out just the package names, sorted, then diffed the two and dumped that list of packages (about 900 or so, IIRC) to apt-get install (then went to bed).  Worked fine, and everything seems to be running as expected so far.

---

### Post by dstein on 2006-06-12
mayostard, can you explain the steps that would be required for me to achieve this? Thanks.

---

### Post by rcarring on 2006-06-12
Midnight Commander can be run from the command line by typing "mc".

It is on the path.

---

### Post by dstein on 2006-06-12
Thanks. I apologize for the basic questions, but is it added to the path when I use apt-get, and also, how can I edit the path, although I probably won't need to. Thanks.

---

### Post by mayostard on 2006-06-12
[QUOTE=dstein]mayostard, can you explain the steps that would be required for me to achieve this? Thanks.[/QUOTE]

OK.  I have two machines, "beowulf" with ubuntu-desktop, and "godel" with ubuntu-server.  This is how I got godel to ubuntu-desktop (the machine is at my office, and I did this all from home).  This is all from memory, but should be pretty close.

1. First, apt-get upgrade both nodes to get the latest versions of everything.

2. apt-get install apt-show-versions (on both nodes, it's not part of the standard distribution)

3. Get list of packages on desktop node:

beowulf> apt-show-versions | sed s'/\/.*$//' | sort > packages_desktop

4. Transfer that file over to the server node:

beowulf> scp packages_desktop @godel:

(or whatever... I have openssh-server on both nodes, you may have to install that or transfer the file some other way)

5. Get list of packages on server node:

godel> apt-show-versions | sed s'/\/.*$//' | sort > packages_server

6. Now diff those, and generate a list of packages that are on the desktop that aren't on the server:

godel> diff packages_server packages_desktop | awk '/^> / {printf $2 " "}' > packages_needed

7. Open packages_needed in your favorite text editor.  You should see a buch of package names all on one line.  Add "sudo aptitude install " at the front of that big line.

8. godel> sh ./packages_needed

it will show the packages to be installed.  answer "yes" then go to bed.  When you wake up, you'll probably have to answer a couple of configuration questions, then wait a little while longer while it configures the new packages.

If you have the desktop CD, you could probably "apt-cdrom add" the CD, then pull the packages off of that instead of pulling them over the network, but since I was doing this remotely I didn't even bother to try that.

---

### Post by confused57 on 2006-06-12
[QUOTE=dstein]Another quick question I forgot to ask:

After I install ubuntu-desktop, will my machine be the same as if I installed the Desktop version rather than the Server or will there still be differences? Also, is there any type of security (virus, spyware) software I should install? Thanks.[/QUOTE]

I suggest you read through some of the articles & HowTo's from the link I gave you earlier,  it should answer most of your questions.

Yes to your 1st question...it should be the same:
sudo aptitude update
sudo aptitude install ubuntu-desktop

No, I don't think so for your 2nd question...there's "firestarter" which is just a frontend GUI that you can configure iptables, which is the firewall that is installed by default by Ubuntu.  For now, I wouldn't worry about anti-virus or anti-spyware...Linux just isn't that susceptible.

---

### Post by ubnoobie on 2006-06-13
if you're comfortable with installing every package that makes up your desktop environment yourself; you can run aptitude from the command line of your server install, and pick & choose the packages you want to install. at a minimum to get going, you'll probably want x-window-system-core and a display manager, such as gdm (if you plan on installing gnome or xfce4), kdm (for kde) or wdm/xdm (a basic display manager).

then, you can look through the 'contents' of the *desktop meta packages (listed below) to get an idea of what the default desktops include. that way you shouldn't miss any of the more important packages. if you enable the universe repository in /etc/apt/sources.list ( see [https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto) ), you'll also find some additional meta packages for 'generic' desktop installations, such as gnome-desktop-environment.


if you are new to deb-based distributions, i would suggest sticking with a default desktop, like you'll find in a default installation of the desktop or alternate cd; or one of these meta packages installed from your console/server installation: ubuntu-desktop (gnome), kubuntu-desktop (kde), or xubuntu-desktop (xfce4).

---

