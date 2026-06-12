---
title: "VMware player"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-02-06
Hello. I recently downloaded VMware player for Linux. However, when I open it, it gives me this message:
> gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.
I am trying to use Windows Vista as a virtual machine (my laptop is licensed for it) but VMware player is not working. Anyone know what the problem is?

---

### Post by davidmohammed on 2011-02-06
open a terminal and run the file downloaded

something like

cd Downloads

sh <filename>

or 


. ./<filename>

---

### Post by towheedm on 2011-02-06
Simply opening the downloaded file does not run it.  The file must first be mounted before installing the player.  The instructions are on the VMWare website.  Check out the getting started guides at:
[http://www.vmware.com/support/pubs/player_pubs.html](http://www.vmware.com/support/pubs/player_pubs.html)

Also, you cannot simply use your existing Win installation as a guest OS.  You must re-install Vista and activate under the player's guess OS.  Now, there is a thread I saw recently, that gave some instructions on using an existing Win installation as the guest OS, but there were some drawbacks to this, such as not being able to boot into it directly afterwards.

---

### Post by TimmyK. on 2011-02-28
OK, I went to the VMware player site, and I am having trouble figuring out what is for installing it with a CD or from the internet. Can someone please give me a simple, concise set of instructions for installing it? Remember, I have never done anything like this before, so don't pre-assume that I know what anything is.

---

### Post by towheedm on 2011-02-28
Could you give the exact name of the file you downloaded and the directory it was saved to?

---

### Post by DanneStrat on 2011-02-28
> **TimmyK. said:**
> OK, I went to the VMware player site, and I am having trouble figuring out what is for installing it with a CD or from the internet. Can someone please give me a simple, concise set of instructions for installing it? Remember, I have never done anything like this before, so don't pre-assume that I know what anything is.


Did you download the appropriate "vmware player for XX-bit linux .bundle" package

from vmware's website?

If you did then that's good, but make sure you

have the latest version.

Let's get started by doing the following:

Place the bundle on your desktop.

Open a terminal and do this:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```Now, change to the directory

you placed the bundle in:

```
cd Desktop
```Now I don't know what version of the bundle

you have, so just put the right package name

in the command below.

[SIZE=4][FONT=monospace][FONT=Arial][SIZE=2]To start the install do:

[/SIZE][/FONT][/FONT][/SIZE]```
[SIZE=4][FONT=monospace][FONT=Arial][SIZE=2]gksudo bash ./[/SIZE][/FONT][/FONT][/SIZE][FONT=Arial][SIZE=2]VMware-Player-X.X.X-XXXXXX.i386.bundle[/SIZE][/FONT]
```[FONT=monospace][FONT=Arial][SIZE=2]

Now you should be presented with a graphical interface

taking you through the installation process.

EDIT: If nothing happens then you may have

to make the file executable.

To accomplish that, in a terminal do:

```


cd Desktop


```

Then do:
[/SIZE][/FONT][/FONT]
```


chmod +x ./VMware-Player-X.X.X-XXXXXX.i386.bundle


```

Now try to run the install again.
[FONT=monospace][SIZE=2]
[/SIZE]


[/FONT]

---

### Post by TimmyK. on 2011-02-28
First of all, when I type in the 

sudo apt-get install build-essential linux-headers- uname -r

it tells me 

E: Command line option 'r' [from -r] is not known.

What do I do?

---

### Post by towheedm on 2011-02-28
Hey TimmyK, there is no need to install build essential and while kudos to DanneStrat for the instructions, it is really a much simpler procedure.

OK, so you downloaded the VMware player file from their site.  The file you downloaded, assuming you downloaded the lastest version would be:

```
VMware-Player-3.1.3-324285.i386.bundle
```

and should, by default be in your downloads directory.

To install the player, please do the following:

1.  Open a terminal window.  Click on Applications > Accessories > Terminal.

2.  Change to your download directory (or whatever other directory you save the file in) by entering the following command:

     ```
cd ~/Downloads
```

3.  In the terminal window, change to root by entering this command and entering your password when prompted:

     ```
sudo su
```

4.  Now, your prompt should change to (or something similar):

     ```
root@GA1A4CH:/home/towheed/Downloads#
```

5.  Now run the installer by entering the followinf command:

     ```
sh VMware-Player-3.1.3-324285.i386.bundle
```

6.  You will now get a GUI installer.  Simple follow the prompts to complete the installation.

7.  When the installation is finished, exit from root in the terminal by entering:

    ```
 exit
```

8.  Run the vmplayer application.  Click on Applications > System Tools > VMware Player

And that's it.

---

### Post by DanneStrat on 2011-02-28
> **TimmyK. said:**
> First of all, when I type in the 

sudo apt-get install build-essential linux-headers- uname -r

it tells me 

E: Command line option 'r' [from -r] is not known.

What do I do?

My mistake.

Do this instead:

```
sudo apt-get update && sudo apt-get install build-essential linux-headers-$(uname -r)

```

Hope this works better.

---

### Post by TimmyK. on 2011-02-28
Got it! Thank you, davidmohammed, towheedm, and DanneStrat!

---

### Post by bloodshot13 on 2011-02-28
> **TimmyK. said:**
> Got it! Thank you, davidmohammed, towheedm, and DanneStrat!
I thank you too! I've been trying for an hour and this did the trick. THANKS!

---

