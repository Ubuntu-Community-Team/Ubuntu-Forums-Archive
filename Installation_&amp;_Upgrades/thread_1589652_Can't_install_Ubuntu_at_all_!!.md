---
title: "Can't install Ubuntu at all !!"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by Parachutee on 2010-10-06
I have done the Wubi installer and used CD's and everytime I install Ubuntu it is successful. When I restarted my computer and go to select Ubuntu all these letters come on the screen like crazy and then at the bottom it says operations stopped. So is it my computer, cause I downloaded and burned it right from the website.

---

### Post by sanderd17 on 2010-10-06
When booting with the live CD, can you press a key when you see a purple screen with an icon of a keyboard and a guy? 

Then try some options from the right most menu (I think F6). If it works, report the options, they'll need to be added after your installation.

---

### Post by Parachutee on 2010-10-06
I am completely lost with what you said, I am really new to linux and have not the slightest of a clue on how to do things. You gotta talk to me like I am just learning.

---

### Post by garvinrick4 on 2010-10-06
What version of Ubuntu are you trying to install WUBI in?

---

### Post by sanderd17 on 2010-10-06
[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/]("http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/")

I mean something like this. The first steps are explained well, follow them to the F6 press, there you'll have to experiment with the availiable options.

If you want to do a wubi install, don't listen to me.

---

### Post by Parachutee on 2010-10-06
The version of Ubuntu I am trying to install is 10.04, the first time I tried to install it was with the Wubi. I have Windows 7 and once I tried it with Wubi and I have the same issue when I burned the iso to a disc and then put it in for the install. Went through the installation successfully. When I went to boot Ubuntu I selected the Ubuntu and it doesn't load up. Did I mention I am setting it up to dual boot with Windows 7. The disc doesn't even let me use the live option where I can try without making any changes to the computer. Is this making sense?

---

### Post by sanderd17 on 2010-10-06
If it doesn't do the live modus, it won't install right. That makes sense. I had a similar problem with a previous ubuntu (I think it was 9.04). I needed to adapt the boot options, which you find easy in the live CD under that F6 menu.

---

### Post by Parachutee on 2010-10-06
Okay I will try that out, thanks for your help and I will let you know if there is any other issues or problems.

---

### Post by Parachutee on 2010-10-06
That worked for being able to view it live and try it out, but when I went to go and install it went through the whole process ejected the cd. I restarted and then clicked Ubuntu and it wouldn't load up it said process stopped. Is the cd bad? Does this sound familiar?

---

### Post by sanderd17 on 2010-10-07
what option did you use in the F6 menu? you may need to add a similar option to your boot commando. 

e.g. if you checked "acpi=off"
start the computer, when you are at the first choice screen, press 'e' to edit. there delete the "quiet" (just to make sure you see the errors if there are any"), there is also something like "splash" you can delete and add "acpi=off" without the quotes.

If you choosed other options, you need to add other parameters to that line.

This is only a temporal change (for 1 boot), once it boots up, you can make the change permanent.

---

### Post by Parachutee on 2010-10-20
Okay, am able to install it and boot from the live cd. when i hit f6 the option i choose for the cd to boot is acpi off. after the installation is complete it wont boot it says something about a kernel what do i do???

---

### Post by sanderd17 on 2010-10-20
great, it's acpi.

acpi is the power control, so switching acpi off will mean you won't be able to use hibernate, I don't know about suspend. You also won't be able to read your battery status (if you use a laptop). If you can live without those things (for at least one release), you should do the following:

When you are in GRUB: press 'e' on the standard line. There you have the boot command, search for "quiet splash" and replace it by "acpi=off". This will allow you to boot once. I now need to do a little search on how to make it permanent, will be back in a minute.

---

### Post by Parachutee on 2010-10-20
okay let me know what you can find

---

### Post by sanderd17 on 2010-10-20
Ok, if the booting succeeded, open /etc/default/grub:

```

sudo gedit /etc/default/grub

```

Then you should see a line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
replace this with
```

GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"

```
Save it and update your grub:
```

sudo update-grub

```

Done, you can now reboot without having to give that option every time.

[I]
Note: this will disable the nice splash screen, if you still want it be enabled, just add the acpi=off in the quotes instead of using it as a replacement for "quiet splash". don't forget to run the update-grub afterwards.
[/I]

---

### Post by Parachutee on 2010-10-20
I think i understand what you are saying and I am going to try this out. I will let you know if I have any issues with it.

---

### Post by Parachutee on 2010-10-20
I tried doing what you said but the problem is there is no kernel, do you think i should just burn the cd all over again and delete the partitions and start from scratch? For some reason it didn't install the kernel so when i got to edit there is no kernel. I am not using the wubi installer, I am using a regular live cd that I downloaded and burned.

---

### Post by sanderd17 on 2010-10-21
so when grub loads, it's an empty menu? If that's the case, I should restart from scratch. This is a weird problem, really weird.

---

