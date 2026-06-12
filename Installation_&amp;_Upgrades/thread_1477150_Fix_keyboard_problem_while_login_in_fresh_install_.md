---
title: "Fix keyboard problem while login in fresh install of Ubuntu in vmware"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by 99Percent on 2010-05-08
How to fix keyboard problem in vmware with Ubuntu 10.0.4 step by step

You may have not be able to log in to your freshly installed Ubuntu 10.0.4 in a vmware virtual machine because there is no keyboard input. This is how to fix it: 

1. At the logon screen click the icon depicting a little man with stretched out arms inside a circle at the botton of the screen (its a very small icon). 

2. A popup menu appears that says [Universal Access Preferences], click on it.

3. A window with several options appear. Select the top option which is [Use on-screen keyboard]. 

5. A white square might flash on the top right of your virtual screen, instead of the actual on screen keyboard. If this happens reboot the virtual machine by clicking on the on/off icon at the bottom right of the screen and then clicking [Restart], and the on-screen keyboard will come up normally upon reboot, otherwise "type" in your password using the mouse.

6. Once logged in go to Applications>Accessories>Terminal and a small terminal screen will appear. with a flashing prompt.

7. Type in the following command: sudo -i 

8. Type in your login password. No text will appear, not to worry, just hit enter when finished.

6. when root@ubunto:~# prompt appears type in the following command: gedit /etc/default/console-setup

7. The text of a configuration file will appear. Scrolldown to the bottom where the following appears:

XKBMODEL="SKIP"
XKBLAYOUT="us"
XKBVARIANT="U.S. English"
XKBOPTIONS=""

8. Edit it to:

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

9. Close and save the file

10. Reboot your virtual Ubuntu 10.0.4 and you should not have any more keyboard problems.

Hope this helped.

(Reference: [http://communities.vmware.com/message/1515622#1515622](http://communities.vmware.com/message/1515622#1515622) )

---

