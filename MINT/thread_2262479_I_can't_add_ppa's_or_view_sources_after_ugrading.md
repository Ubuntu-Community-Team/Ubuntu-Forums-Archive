---
title: "I can't add ppa's or view sources after ugrading"
date: 2015-01-25
forum: MINT
---

### Post by markackerman8@gmail.com on 2015-01-25
I have just installed for the 4th or 6th time Linux Ultimate Cinnamon Mint distro and always after the first updates me sources list is kyboshed.

I can't ad ppa's from command line, view sources from the menu, or open them from synaptic either.
Please help me troubleshoot as I have READ EVERY google hit and there are an infinite number of reasons that can cause this and just as many solutions it appears.

please help me it is so frustrating:mad:

for the record it's mint cinnamon based on trusty 14.04 gnome 3 (no unity - YEAH)
and anything I can do to help he troubleshooting will be soo helpful - i have instant email notification

---

### Post by nerdtron on 2015-01-25
Any errors on the command line? Screenshot of errors on GUI synaptic?

---

### Post by markackerman8@gmail.com on 2015-01-25
$ sudo add-apt-repository ppa:vovansrnd/coolreader
[sudo] password for ack: 
Traceback (most recent call last):
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 1258, in <module>
    codename = config_parser.get("general", "base_codename")
  File "/usr/lib/python2.7/ConfigParser.py", line 330, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'general'


everything always seems to point to mintSources.py

and perhaps a conflict with ubuntu and mint's distro names in certain config files (is a guess)

---

### Post by markackerman8@gmail.com on 2015-01-25
$ software-sources 
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 1262, in <module>
    Application().run()
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 559, in __init__
    if self.config["general"]["use_ppas"] == "false":
KeyError: 'general'


and in Synaptic
 $ sudo synaptic

(synaptic:9111): Gtk-CRITICAL **: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed
Traceback (most recent call last):
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 1262, in <module>
    Application().run()
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 559, in __init__
    if self.config["general"]["use_ppas"] == "false":
KeyError: 'general'

---

### Post by markackerman8@gmail.com on 2015-01-25
ack@Aarawn ~ $ software-sources 
    Application().run()
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 559, in __init__
    if self.config["general"]["use_ppas"] == "false":
KeyError: 'general'

and when selecting repositories from synaptic .... the same thing
ack@Aarawn ~ $ sudo synaptic

(synaptic:9376): Gtk-CRITICAL **: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed
Traceback (most recent call last):
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 1262, in <module>
    Application().run()
  File "/usr/lib/linuxmint/mintSources/mintSources.py", line 559, in __init__
    if self.config["general"]["use_ppas"] == "false":
KeyError: 'general'

---

### Post by markackerman8@gmail.com on 2015-01-25
AND SOMEBODY SUGGESTED

ack@Aarawn ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ack@Aarawn ~ $ sudo apt-get -d dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

BUT  NO HELP

---

### Post by mc4man on 2015-01-25
Where did you get this so called 'distro' from? 
I'm guessing this one - [http://sourceforge.net/projects/ultimatelinuxmintcinnamon/](http://sourceforge.net/projects/ultimatelinuxmintcinnamon/)
If so it appears that it's more for what you get is what you'll use, I see you posted here also - 
[http://www.linuxforums.org/forum/mint-linux/202669-ultimate-linux-mint-17-cinnamon-edition-64-bit.html](http://www.linuxforums.org/forum/mint-linux/202669-ultimate-linux-mint-17-cinnamon-edition-64-bit.html)

Edit: generally not a great idea to use your email as a user name...

---

### Post by oldos2er on 2015-01-25
Moved to Other OS Support and Projects.

You may want to seek help on Mint's forums: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by ibjsb4 on 2015-01-25
> for the record it's mint cinnamon based on trusty 14.04 gnome 3 (no unity - YEAH)
I also had glitching with mint and switched to mate.
Mate is suppose to become an official ubuntu flavor, works well for me.  And yes, no unity :)

---

