---
title: "can't view login in screen using 15&quot; monitor"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by isaac on 2005-02-07
HI,

    I'm new to Ubuntu and i need some help viewing my login page.

     I have use a 17inch monitor to install everything and it works ... ubuntu is great. but when i change my monitor to 15inch i can't view my login page... I have tried and change the resolution to 800x600 and also 1024x768 which was the max resolution for my 15inch monitor... but i still can't view the login screen ... making me hardly can login into ubuntu... 

    But i can view the workspace in ubuntu using 15" . this can be only done by using my 17inch monitor to view the login screen to key in my apssword then change back to my 15' monitor... 

   I think is the login sreen resolution in higher then 1024x768 making my 15' monitar unable to view it. but How can i change the login screen resolution?


    Pls help ... thanks in advance

---

### Post by Wim Sturkenboom on 2005-02-07
You have to modify a few settings in XF86Config-4.

HorizSync and VertRefresh in your monitor section should reflect what your monitor is capable of. You should check the monitor manual for the correct values. I seem to remember that these will influence the initial resolution that X uses (your login screen).

Next there are a couple of lines like Modes "1152x864" "1024x768". Remove any modes that you don't want. As your monitor can handle it, you can leave 1024x768 in. This will be used for the login.

When Gnome starts, it will use the resolution that you chose using the settings in the desktop menu..

---

