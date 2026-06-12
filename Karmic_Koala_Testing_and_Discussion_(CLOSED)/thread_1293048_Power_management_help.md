---
title: "Power management help"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by drfox on 2009-10-16
I have an HP notebook with power management settings to go to suspend if the lid is closed or if the power button is pressed. It will not suspend (or hibernate, I checked that too) when I close the lid. It will only suspend if I mouse-click on the shutdown icon and choose suspend. Moreover, if I press the power button, I get a strange error message that pops up and says "Action disallowed. Suspend support has been disabled. Contact your administrator for more details."

Any ideas to try to troubleshoot? Thanks.

---

### Post by wrtrdood on 2009-10-17
Similar issue here.  I'm running on an AMD 64 HP Pavilion dv6700.  I've only seen my laptop suspend on lid close two or three times if I'm logged in.  When I log out and close the lid it works every time (although resume is usually a two cycle open/close process ...odd).

I tried with a generic login thinking there was something in my configuration causing the problem but it didn't make any difference.  I turned off compiz with no change.  Not sure what the deal is but I'm still looking.  Haven't tried the power button route.  I'll check that soon.  It was not suspending or hibernating with the manual button click either but I've not tried it recently.  I'll do some more testing to see if I can replicate your symptoms.
\
Nope.  Power button pops up the power management menu and clicking the suspend button tries but does not succeed.  My symptoms here for both suspend and hibernate is a black screen with flashing cursor in the upper left corner for approximately 10 seconds then it returns to normal.  I know it's trying because the wireless network has to reconnect.

---

### Post by drfox on 2009-10-17
I figured it out...
Go to Applications>System Tools>Configuration Editor>apps>gnome-power-manager>general
Enable (by clicking on the check box) can_hibernate and can_suspend
Close the Configuraton Editor and everything is as you expect it to be.

Hope this helps others.
Larry

---

### Post by wrtrdood on 2009-10-17
Good catch.  Unfortunately mine is not that easy (already selected).  Still digging...

---

