---
title: "No Unity 3D on new Natty install"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by faillord adam on 2011-04-29
This is my first post.

I've just installed Natty Narwhal onto my laptop, but I cannot find Unity 3D, only 2D. I've installed the propriety NVIDIA drivers, but there still is no 3D option.

I've also seen no one who likes Unity, but I do.

---

### Post by 23dornot23d on 2011-04-29
Welcome .....

What laptop is it that you use ... ?

and what graphics card ..... ?

---

### Post by faillord adam on 2011-04-29
> **23dornot23d said:**
> Welcome .....

What laptop is it that you use ... ?

and what graphics card ..... ?
Acer Aspire 5630
NVIDIA GeForce Go 7300

---

### Post by 23dornot23d on 2011-04-29
Cheers ...

Can you run nvidia-settings at all ...... ?

Administration  >>> Nvidia X server Settings

---

### Post by C++buntu on 2011-04-29
Hi everyone, 

I have the same problem here. I was able to run the full 3D effects under Ubuntu 10.10. I have a Dell Latitude D820 with a NVIDIA NVS120M graphic card...

When I look in the Additional Drivers, I have two choices of drivers, namely:

-NVIDIA accelerated graphics driver (version 173)
-NVIDIA accelerated graphics driver (version current) [recommended]

When I install the version current and restart, it says that the driver is activated but not in use...what can i do?

Thanks!

---

### Post by 23dornot23d on 2011-04-29
I have a feeling that the driver is being stopped in gdm ..... ( why I do not know yet ) but .....

I always swap to kdm as the boot up for mine ...... to the kdm Menu .....

Gnome and Unity will still run ..... as normal and you will get a different menu 

go into a terminal and type the following ......

[COLOR=Red]**sudo apt-get install kdm**[/COLOR]

choose kdm when it asks you ...... let me know what happens ......
( by the way if you do not like it or it is not making any difference you can easily change back to gdm )

You will have to re-boot to see the change here .....

---

### Post by faillord adam on 2011-04-29
> **23dornot23d said:**
> Cheers ...

Can you run nvidia-settings at all ...... ?

Administration  >>> Nvidia X server Settings
I can run it, and now selecting Ubuntu as my Desktop Enviorment will use Unity, where as before I was using Unity 2D. I think my problem has been solved.

---

### Post by C++buntu on 2011-04-29
> **faillord adam said:**
> I can run it, and now selecting Ubuntu as my Desktop Enviorment will use Unity, where as before I was using Unity 2D. I think my problem has been solved.

I can run it too, but I can't use Unity yet. I will try the KDM trick...and let you know.

---

### Post by 23dornot23d on 2011-04-29
@ Faillord adam

Hope it is ok ....

If it is solved go to **[COLOR=Red]Thread Tools[/COLOR]** in red scroll towards the top of the page click the drop down button/tab and choose solved ......

@C++buntu

if kdm does not work or you do not like it  ...... then to remove it .....

[COLOR=Red]sudo apt-get remove kdm[/COLOR]

Then select gdm when it asks you which you want to use  .........

or if its ok just keep it ..... again hope its all working ok .....

---

### Post by C++buntu on 2011-04-29
> **23dornot23d said:**
> @ Faillord adam

Hope it is ok ....

If it is solved go to **[COLOR=Red]Thread Tools[/COLOR]** in red scroll towards the top of the page click the drop down button/tab and choose solved ......

@C++buntu

if kdm does not work or you do not like it  ...... then to remove it .....

[COLOR=Red]sudo apt-get remove kdm[/COLOR]

Then select gdm when it asks you which you want to use  .........

or if its ok just keep it ..... again hope its all working ok .....

it does'nt work...yet ;)

---

### Post by 23dornot23d on 2011-04-29
@C++buntu (you have hijacked someone elses thread - you should really start a new one and give me a link to it ..... unless this has been solved)
which it has - in which case we can carry on .....

Ok can you do a screenshot of when you have the Nvidia-settings up .... presuming you have a Nvidia graphics card - if not which graphics card do you use ?

---

