---
title: "Ubuntu 12.04 Package Minicom"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by countryboy456 on 2013-07-31
I have searched but cannot find a resolution to this.

I am trying to use Ubuntu 12.04 to program my Cisco Switch.

At this time, I know I need the minicom package installed on the OS.

When I use the command it says:

ubuntu@ubuntu:~$ sudo apt-get install minicom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package minicom

I have seen in past logs where I need to go into the Ubuntu Software Center, and add the Universal repo..

I have opened the Universal Installer multiple times, and cannot find the options to add repo's into it.

I can see where I can search in it, and when I do, I do not see the package minicom.

Anything I can do to get the Universal Repo added to where I can install Minicom?

Thank you for your help.

**NOTE: I have searched the internet, and Ubuntu, along with other Linux forums for this information, but am not able to find information that I am needed in Ubuntu 12.04.  If this is already been answered, please let me know.

Thank you, 
Kenneth

---

### Post by mojo706 on 2013-07-31
Hello, The Package > minicom is in the [repos ]("http://packages.ubuntu.com/precise/minicom") (I searched online packages for Precise) (see my terminal screenshot)

[IMG]http://i.imgur.com/OViEBEC.png[/IMG]

so try 

```
sudo apt-get update
```

from the terminal.

Any more questions just ask!

---

### Post by mojo706 on 2013-07-31
About the question to add Universal repos. Follow this steps
* Open Ubuntu Software Centre

*In the menu got to edit -> software sources

* A dialog box is opened (view screenshot)
[IMG]http://i.imgur.com/mez8jsO.png[/IMG]

* See if you have checked the relevant check box

* after choosing the option you want update package info to include new software sources ```
sudo apt-get update
``` then search for *minicom* again.

Hope this works!

---

### Post by countryboy456 on 2013-07-31
@[**[COLOR=#000000]mojo706[/COLOR]**]("http://ubuntuforums.org/member.php?u=1303015"), Yes, I have done the 'sudo apt-get update' command before trying to install minicom. 

As far as the Ubuntu Software Center goes, I open it up, but for the life of me I cannot find the menu, button, I found 'Universal' on the left hand side, and i searched in there with no success. I looked at the top of the program as well, but no luck on trying to see an edit button, just previews of apps, that Ubuntu displays.. Could you tell me where exactly the 'Menu' button is at? that is where I am really lost.

I am not at home at this time as well, but I will search when I do.

I apologize for my ignorance, and I do thank you for your time and wisdom.

---

### Post by mojo706 on 2013-07-31
@countryboy456, ok do search when you get the time.

---

### Post by countryboy456 on 2013-07-31
**@**[URL="http://ubuntuforums.org/member.php?u=1303015"][B][COLOR=#000000]mojo706


This is the screen that I see. Where would the Menu button be at?


[/COLOR][/B][/URL][[ATTACH=CONFIG]244960[/ATTACH]]("http://ubuntuforums.org/member.php?u=1303015")

---

