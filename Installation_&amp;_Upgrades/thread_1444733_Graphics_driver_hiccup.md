---
title: "Graphics driver hiccup"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by goldenEY3 on 2010-04-01
Hey all,
I'm brand new to Ubuntu, and am having a small problem. I'm trying to run a graphics card driver instillation, but whenever I run the file, it says that it has to run as a root. How do I run the file as a root?
The graphics card I have is an Nvidia 8800GTM.

---

### Post by Naggobot on 2010-04-01
Hello and welcome to forums. 

I personally am not familiar with Nvidia drivers but before installing anything directly I would recommend that you check

System -> Administrations -> Hardware Drivers

If I am not mistaken the system should find the correct driver for you that way with out any hazzle. Generally in Ubuntu you do not need to download files from Internet and install them. All of the stuff is can be found from the synaptic package manager or software center, except proprietary drivers which are installed as described above. 

I may be mistaken, if so then the command you are looking for is sudo ie. you need to open terminal and then type sudo +command.

---

### Post by quadproc on 2010-04-01
> **goldenEY3 said:**
> Hey all,
I'm brand new to Ubuntu, and am having a small problem. I'm trying to run a graphics card driver instillation, but whenever I run the file, it says that it has to run as a root. How do I run the file as a root?
The graphics card I have is an Nvidia 8800GTM.
No problem.  Find the full path to the driver install file.  Start a terminal (from Applications > Accessories > Terminal if you don't have one on the top bar).  In the terminal, type
```
cd <the_path_to_the_install_file>
```In the terminal, type
```
sudo chmod 777 <name_of_install_file>
sudo sh <name_of_install_file>
```substituting the appropriate names for the strings indicated by <stuff> (don't include the <> characters).

The system will ask you for your password because you are going to modify some system things so type in your normal login password.

The install script will now run.  It should announce what it is doing and when it completes.

The chmod may be necessary to give execute permissions to the install script; it won't hurt even if not needed.  The sudo command means "super user do" and gives root privilege to the remainder of your command.

quadproc

---

### Post by goldenEY3 on 2010-04-04
Thanks for the help, but I think I'm doing something wrong here.
Not sure I can describe it, so here's a snapshot.

---

### Post by Naggobot on 2010-04-05
All I can think of that there is some typo on the name. Could of course be some other reason. 

I think you could try following

Open terminal
Applications -> Accessories -> Terminal

type

```
gksudo nautilus
```this will open a file manager instance for you with root privileges. Next you need to use the file manager to find your desktop and the file which should be located in. 

/home/*your home directory*/Desktop/

Highlight the file and press enter to run the script. A pop up window will open asking you whether you want to execute the script or edit it, select execute.

This way you do not need to worry about the possible typos. Be extra careful while using the file manager with root privileges so that you do not accidentally move system files or do something else unwanted. 

Now before doing this make sure that you have read through the possible installation instructions provided by Nvidia. As I said previously I am not familiar with the installation procedure of the driver but for some reason I have a bad gut feeling about this. Perform above command only if you are absolutely sure that you have correct file vs. graphics card and that the installation method you are attempting is correct. 

I also admit now before hand that I am most likely unable to help you if something goes wrong since I am a noob my self. This is also why I am warning so much about this.  I my self am an expert at fiddeling with things so that they get messed up and somehow this has word *problem* written all over it.

Be mindful of what you do and you should be OK ;).

---

### Post by goldenEY3 on 2010-04-06
Thank you! Turns out I was also missing a period in the code. Reminds me why I'm not a programmer.

---

