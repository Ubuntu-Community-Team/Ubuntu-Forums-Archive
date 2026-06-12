---
title: "ububtu 10 boot problem"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by joymarie on 2010-10-18
[SIZE=3][FONT=Courier New]hi,
i have recently downloaded and installed the latest ubuntu for desktop. i am using intel pentium P6100.
anyway, i had used wubi to install it inside vista.
the installation was fine until i reached grub where there was three options.
1. the ububtu, linux generic
2. the ubuntu, linux recovery
and 
3. vista

so then i chooses the first option.
it did nothing but load stuff in the black screen and kept asking for my login account.

since im a novice, i was kind of frustrated because i couldn't go directly to the system.

please help me.

im kinda exited to use the o.s.

thanks :guitar:
 
[/FONT][/SIZE]

---

### Post by JackNocturne on 2010-10-18
hello,

When you click the first option i.e Linux generic does it boot in text mode?

When you are at the login prompt, type your Account name & password, if **success login** you see something like [PHP]accountname@computername:~$ [/PHP]  ,when you are at that stage type ```
startx
```

---

### Post by joymarie on 2010-10-18
[SIZE=2][FONT=Courier New]hey thanks for the answer.
i'll reboot my laptop now and see it from there. 
get back to u in a jiff.
:guitar:
[/FONT][/SIZE]

---

### Post by joymarie on 2010-10-18
> **JackNocturne said:**
> hello,

When you click the first option i.e Linux generic does it boot in text mode?

When you are at the login prompt, type your Account name & password, if **success login** you see something like [PHP]accountname@computername:~$ [/PHP]  ,when you are at that stage type ```
startx
```


[SIZE=2][FONT=Courier New]i[/FONT][/SIZE] have tried what yous said.
but it only load black screen.
what does it mean?

i interrupted the process after 10 minutes.

---

### Post by JackNocturne on 2010-10-18
That means there is a **problem** with graphic drivers, unfortunately i'm inexperienced in that area, but don't worry someone will provide a solution.:P

Add the following info too, after you **login** as before (without startx command)
type
```
lspci | grep -i graphic

```Tell us the output,that will display your graphic card/controller.

---

### Post by joymarie on 2010-10-18
> **JackNocturne said:**
> That means there is a **problem** with graphic drivers, unfortunately i'm inexperienced in that area, but don't worry someone will provide a solution.:P

Add the following info too, after you **login** as before (without startx command)
type
```
lspci | grep -i graphic

```Tell us the output,that will display your graphic card/controller.

[SIZE=2][FONT=Courier New]it still doaesnt work.
what do i have to do then? 

[/FONT][/SIZE]

---

### Post by JackNocturne on 2010-10-18
i'm sorry, i wasn't very clear, i mean that command ```
lspci | grep -i graphic
```
will tell you what is the name of your graphics card. By knowing the name of your graphics card, we will be able to find drivers for it.

---

### Post by rebecca1986618 on 2010-10-18
i learn more from this forum.

---

### Post by Don544 on 2010-10-18
Similar problem here. My machine offers five options ,after trying all five I found one line loads Ubuntu,as a graphical os. another loads the recovery mode another ends with a command line system after loading  and two seem to point no where. I  was about to post a thread about that and password problem.
Don

---

### Post by JackNocturne on 2010-10-18
Don,
what are the other **options** which dont load to nowhere? and what password problem are you talking about?

---

### Post by joymarie on 2010-10-18
> **JackNocturne said:**
> i'm sorry, i wasn't very clear, i mean that command ```
lspci | grep -i graphic
```will tell you what is the name of your graphics card. By knowing the name of your graphics card, we will be able to find drivers for it.

[SIZE=2][FONT=Book Antiqua]hello,
here's the result after the command lspci | grep -i graphic:

[/FONT][/SIZE][COLOR=Black][B]00:02 0  VGA Compatible Controller: Intel Corporation Core Processor Integrated 
Graphics Controller 
(rev 18)
[/B][/COLOR] 
that's it.
kindly help me fix my graphics problem.
i don't want to do anything until im sure of help.
thanks

---

### Post by joymarie on 2010-10-18
> **Don544 said:**
> Similar problem here. My machine offers five options ,after trying all five I found one line loads Ubuntu,as a graphical os. another loads the recovery mode another ends with a command line system after loading  and two seem to point no where. I  was about to post a thread about that and password problem.
Don


[SIZE=2][FONT=Book Antiqua]i know what you mean. 
you hit ESC key when you had chosen to load the first grub right?
i have tried that too. 
and i dont even know what the terminal is trying to ask from me.
there are a lot of commands which, of course, i am wasn't aware of.



[/FONT][/SIZE]

---

### Post by joymarie on 2010-10-18
**hi, sorry it's (rev18)**

---

### Post by drs305 on 2010-10-18
I am not a graphics troubleshooter, but here is something you can try:

At the Grub menu, highlight "Ubuntu Linux Generic". Press "e".
This will display the menu entry. Look for a line similar to this. The numbers will be different:

> linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro   quiet splash

Add this at the end of the "linux" line:  **nomodeset**
It should now look something like this:
> linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro   quiet splash **nomodeset**

Now press CTRL-x and see if you get some (low-res) graphics.

---

### Post by joymarie on 2010-10-18
> **joymarie said:**
> [SIZE=2][FONT=Book Antiqua]hello,
here's the result after the command lspci | grep -i graphic:

[/FONT][/SIZE][COLOR=Black][B]00:02 0  VGA Compatible Controller: Intel Corporation Core Processor Integrated 
Graphics Controller 
[/B](rev 18)
[/COLOR] 
that's it.
kindly help me fix my graphics problem.
i don't want to do anything until im sure of help.
thanks


,
hi it's (rev eighteen).

---

### Post by joymarie on 2010-10-18
> **drs305 said:**
> I am not a graphics troubleshooter, but here is something you can try:

At the Grub menu, highlight "Ubuntu Linux Generic". Press "e".
This will display the menu entry. Look for a line similar to this. The numbers will be different:



Add this at the end of the "linux" line:  **nomodeset**
It should now look something like this:


Now press CTRL-x and see if you get some (low-res) graphics.


[SIZE=2][FONT=Book Antiqua]hi,
i tried it but it still does not work.
does that mean my pc is lacking something?
a driver perhaps?
[/FONT][/SIZE]

---

### Post by drs305 on 2010-10-18
> **joymarie said:**
> hi,
i tried it but it still does not work.
does that mean my pc is lacking something?
a driver perhaps?


The nomodeset option is used to boot into a system having graphics issues so that the user can then install the appropriate drivers. I'll have to leave the graphics answers to users more knowledgeable in that area.

Are you just facing a blank screen or are you still having username and password login difficulties?

---

### Post by joymarie on 2010-10-19
> **drs305 said:**
> The nomodeset option is used to boot into a system having graphics issues so that the user can then install the appropriate drivers. I'll have to leave the graphics answers to users more knowledgeable in that area.

Are you just facing a blank screen or are you still having username and password login difficulties?


[SIZE=2][FONT=Courier New]hello,
after i added the nomodeset and press ctrl x to boot, the system asked for my login account, i entered it, then it is again asking for a command. i tried the command startx and i only get the blank screen.
i restart the pc after 10 minutes. 
i'm afraid it will damage my hd, with restarting a lot of times.
[/FONT][/SIZE]

---

### Post by drs305 on 2010-10-19
I don't know what the problem is. If you don't have data files or lots of time invested in customizing your Wubi install you might consider reinstalling Wubi to see if that corrects the problem. 

If you decide to do this, you uninstall the existing Wubi via the Windows Control Panel, Add Remove option.

If you have important data inside Wubi, we can tell you how to mount the Wubi file to recover those files.

---

### Post by joymarie on 2010-10-19
> **drs305 said:**
> I don't know what the problem is. If you don't have data files or lots of time invested in customizing your Wubi install you might consider reinstalling Wubi to see if that corrects the problem. 

If you decide to do this, you uninstall the existing Wubi via the Windows Control Panel, Add Remove option.

If you have important data inside Wubi, we can tell you how to mount the Wubi file to recover those files.


[SIZE=2][FONT=Book Antiqua]i have no files at ubuntu yet.
i have tried re-installing it.
same thing happen.
[/FONT][/SIZE]

---

