---
title: "Fixing Pepper Flash Plugin"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by EarendilTheMariner on 2015-02-19
Three problems with OMG! Ubuntu fix for Pepper Flash Plugin
                         
                        

     I got some recent help uninstalling my Chrome browser, and now I'm running Chromium on Xubuntu 14.04 and need to install the PAPPI (Pepper) Flash plugin.  
  
 
      But  I havethreesmall problems with the following link from OMG! Ubuntu, [http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04)      
  which gives you instructions on how to fix Pepper Flash if the installation did not work, which I hope will not happen.  But considering the recent crashes I have experienced, I'm preparing for the worst.

  
 
      First, my text editor is not called gedit, but nano.
  
 
      Second, his instructions for the second command line would make more sense if he said &#8220;Type the following line at the beginning of a new line.&#8221;  Not the end.
  
 
      Thirdly, since I'm using a different text editor, I assume saving the file I just created may be different.  I suspect there may be two ways to save it.  One would be to press Esc to enter command mode, and then type ":wq!" to save the document and quit command mode.  The other would be to just type Control + X, and say yes, when the nano text editor asks me to save the modified buffer.  That should save the file and bring me back to the command prompt.
  
 
      Am I right?
  
 
      I have never tried the first, so I would rather try the latter Ctrl X method, since I've done it before with another Chrome-related fix.  I'm just an Ubuntu neophyte, so I was just spoonfed the command lines with that last fix.

  
 
      Ok, so here's a summary of his instructions versus mine.  Tell me if my method would work better using the nano text editor, and if I made any mistakes, if you please.  I need the feedback, because I'm still learning how to use the command lines for Ubuntu.
  
 
  OMG! Ubuntu:
  run the following command in a Terminal to launch the appropriate file in a text editor:
 sudo gedit /etc/chromium-browser/default Add the following line at the end on a new line:
 . /usr/lib/pepflashplugin-installer/pepflashplayer.sh Save &#8212; it&#8217;s easy to forget to do that &#8212; and then close.  
  <EarendilTheMariner:
             1.  open a terminal.
      2. type "sudo nano /etc/chromium-browser/default" and hit enter
  3. Type the following line at the beginning of a new line:
  
 
 . /usr/lib/pepflashplugin-installer/pepflashplayer.sh
 
 
  4.  type Control + x
  5. Then say yes when it asks to save the modified buffer
      6. That should save it and bring you back to the command console.  Exit it command console.
  
 
  By the way, that period and space before the forward slash is weird.  I never seen that before.  Is that a typo?
  
Sincerely,
EarendilTheMariner

---

### Post by Bucky Ball on 2015-02-19
Don't know about OMG!, but pepperflashplugin-nonfree is in the repositories. That should install it without a hitch. Should be no need to install it manually, use commands in the terminal or drag in third-party PPAs.

---

### Post by coffeecat on 2015-02-19
> **EarendilTheMariner said:**
> 
 
      First, my text editor is not called gedit, but nano.

That's because the omgubuntu instructions are for Ubuntu and you are using Xubuntu. Gedit is the default GUI text editor for Ubuntu - Xubuntu uses mousepad (I believe - can a Xubuntu user confirm this?) There is nothing wrong with using nano except that it is not as user-friendly as a GUI text editor such as gedit or mousepad. Simply substitute mousepad for gedit (if I am correct about mousepad being the default Xubuntu editor) in those instructions and you should be OK. Or rather, not quite. The omgubuntu page you link to suggests:

```
sudo gedit /etc/chromium-browser/default
```

That's horrible. You should not use sudo without options with GUI apps, as described here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You have two options if you need to edit a system file with root privileges in a GUI editor in Xubuntu. 

1 - install the package gksu (if not already installed) and run:

```
gksu mousepad <path-to-file>
```

2 - Or:

```
sudo -H mousepad <path-to-file>
```

---

### Post by slickymaster on 2015-02-19
> **coffeecat said:**
> That's because the omgubuntu instructions are for Ubuntu and you are using Xubuntu. Gedit is the default GUI text editor for Ubuntu - Xubuntu uses mousepad (I believe - can a Xubuntu user confirm this?) There is nothing wrong with using nano except that it is not as user-friendly as a GUI text editor such as gedit or mousepad. Simply substitute mousepad for gedit (if I am correct about mousepad being the default Xubuntu editor) in those instructions and you should be OK. Or rather, not quite.
You're absolutely corrct coffeecat, Mousepad is the default text editor shipped in Xubuntu. 
> **coffeecat said:**
> The omgubuntu page you link to suggests:

```
sudo gedit /etc/chromium-browser/default
```

That's horrible. You should not use sudo without options with GUI apps, as described here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You have two options if you need to edit a system file with root privileges in a GUI editor in Xubuntu. 

1 - install the package gksu (if not already installed) and run:

```
gksu mousepad <path-to-file>
```

2 - Or:

```
sudo -H mousepad <path-to-file>
```
Just to point out that all default applications shipped in Xubuntu that might need to be ran with administrative rights come, since [s]Trusty Tahr[/s] Utopic Unicorn release, with **pkexec** policy files. So in this case to run Mousepad with administrative rights, the OP just needs to run the command```
pkexec mousepad /path/to/file

```

---

### Post by ajgreeny on 2015-02-19
Yes, it's mousepad for Xubuntu now.

It was leafpad in Xubuntu up to at least 12.04, but as you say, it doesn't matter which you use, they are all text editors, including nano, which is usually my choice for editing system files that need root permissions.

Thanks also to slickymaster for the info about **pkexec mousepad**.  I was aware that pkexec was taking over from gksu, but I had not caught up with the fact that mousepad was one of the applications for which it works.

Is there a list of those apps that do and those that don't have pkexec policy files?
All I could find from a locate command was:-

/usr/bin/gparted-pkexec
/usr/bin/pkexec
/usr/bin/synaptic-pkexec
/usr/share/man/man1/pkexec.1.gz
/usr/share/polkit-1/actions/com.ubuntu.pkexec.gparted.policy
/usr/share/polkit-1/actions/com.ubuntu.pkexec.synaptic.policy

with no mention of mousepad, though I have just tried it and it works.

PS: I already have an alias of 
**pkx=pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY** 
which seems to work for all apps I've tried, so I have been using pkexec for a while using that workaround.

---

### Post by coffeecat on 2015-02-19
> **slickymaster said:**
> You're absolutely corrct coffeecat, Mousepad is the default text editor shipped in Xubuntu. 

Just to point out that all default applications shipped in Xubuntu that might need to be ran with administrative rights come, since Trusty Tahr release, with **pkexec** policy files. So in this case to run Mousepad with administrative rights, the OP just needs to run the command```
pkexec mousepad /path/to/file

```

Well, yes, I would agree with the use of pkexec in the ideal, ivory tower, world that devs inhabit, the world that prompted the "who on earth would want to use gedit for editing system files when one has vi or emacs" (I paraphrase) comment when a bug involving a root-owned gedit remained unfixed for years. My problem is that Ubuntu does not have a pkexec policy file for gedit by default and I suspect that Xubuntu might not have one for mousepad, but I would be happy to be corrected on that latter point. So my pragmatic world approach when trying to help relatively inexperienced people is to recommend gksu or sudo -H.

Try getting a newbie to create the file /usr/share/polkit-1/com.ubuntu.pkexec.gedit.policy with these contents:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
  "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
  "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.gedit">
    <message gettext-domain="gparted">Authentication is required to run gedit</message>
    <icon_name>gedit</icon_name>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/gedit</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
``` 

:|

---

### Post by slickymaster on 2015-02-19
Just a correction to my previous post, it's since Utopic Unicorn that Xubuntu started to ship pkexec instead of gksudo for running graphical applications with root access from the terminal for improved security. 
> **ajgreeny said:**
> Yes, it's mousepad for Xubuntu now.

It was leafpad in Xubuntu up to at least 12.04, but as you say, it doesn't matter which you use, they are all text editors, including nano, which is usually my choice for editing system files that need root permissions.

Thanks also to slickymaster for the info about **pkexec mousepad**. I was aware that pkexec was taking over from gksu, but I had not caught up with the fact that mousepad was one of the applications for which it works.

Is there a list of those apps that do and those that don't have pkexec policy files?
<---snip--->
The contemplated applications were Mousepad and Thunar.
> **coffeecat said:**
> Well, yes, I would agree with the use of pkexec in the ideal, ivory tower, world that devs inhabit, the world that prompted the "who on earth would want to use gedit for editing system files when one has vi or emacs" (I paraphrase) comment when a bug involving a root-owned gedit remained unfixed for years. My problem is that Ubuntu does not have a pkexec policy file for gedit by default and I suspect that Xubuntu might not have one for mousepad, but I would be happy to be corrected on that latter point. <---snip--->
To allow users to use pkexec for the selected applications, instead of gksu(do), the appropriate profiles were included for both Thunar and Mousepad.

---

### Post by ajgreeny on 2015-02-19
I've just tried **pkexec mousepad** again and this time it did not work (in Trusty) nor does **pkexec tunar**

However my alias does work for all applications that I have tried with it.

Very often, I have to admit, I do still use **gksu** or **gksudo**, just like many others do, I imagine, simply because I have got so used to using that and it is difficult to change old habits; I work on autopilot sometimes as most people do and have typed commands before I've thought about what I am doing in enough detail.

---

### Post by slickymaster on 2015-02-19
> **ajgreeny said:**
> I've just tried **pkexec mousepad** again and this time it did not work (in Trusty) nor does **pkexec tunar**
<---snip--->
That is expected as pkexec was only brought in during the Utopic cycle.

---

### Post by coffeecat on 2015-02-19
> **slickymaster said:**
> To allow users to use pkexec for the selected applications, instead of gksu(do), the appropriate profiles were included for both Thunar and Mousepad.

Good to hear that the Xubuntu devs are ahead of the curve about this. Thanks. For the record, my Ubuntu 14.10 installation didn't have a pkexec profile by default for gedit and I had to create the file I detailed in my earlier post to be able to use "pkexec gedit".

**Edit:** Nor does Ubuntu 14.10 have a pkexec profile for nautilus. All, of course, off-topic for the OP but it's useful to know the pkexec differences between the flavours.

---

### Post by ajgreeny on 2015-02-19
Just to round this off, and for information for you all, I have just this minute created two policy files, one for mousepad and a second for thunar, using exactly the text and syntax shown in coffeecat's post #6, added them to **/usr/share/polkit-1/actions**, which is where Xubuntu puts these files, and I can report that both applications now open with root permissions using command **pkexec mousepad **or **pkexec thunar**

---

