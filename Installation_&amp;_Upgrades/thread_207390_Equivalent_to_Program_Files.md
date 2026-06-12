---
title: "Equivalent to Program Files"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by harryhoudini66 on 2006-07-01
I downloaded Azureus and am not sure where to put it. I left it on my Desktop and got it to work. I am just wondering where it should be placed though. I want it to be accessible to everyone once I setup additional users. I will need to do this for other programs I plan on installing.

Also, once I get it in the right location, how do I get the Azureus.png to show as an icon? I want to add it to Internet folder.

Thanks

---

### Post by Nonno Bassotto on 2006-07-01
How did you install it? You can install Azureus through the repositories: look for
System->Administration->Synaptic package manager
Through it you can install Azureus for all users, and it will show up in the menu. Moreover you will get updates and you will be able to uninstall it cleanly.

PS
If you don't find Azureus, you have to enable universe and multiverse repositories. Open System->Administration->Software properties and check the boxes which are not checked.

---

### Post by Nonno Bassotto on 2006-07-01
Of course this does not apply only to Azureus, this is the "correct" way to install software in Ubuntu. You can search here your new software, this is one of the main strength of linux over windows.

---

### Post by harryhoudini66 on 2006-07-02
Thanks for the info. I had downloaded it from the net ans extracted it to my desktop. I did not know it was in the reposatory. Will replace it now.

Thanks again.

---

### Post by lepre on 2006-07-03
[QUOTE=Nonno Bassotto]How did you install it? You can install Azureus through the repositories: look for
System->Administration->Synaptic package manager
Through it you can install Azureus for all users, and it will show up in the menu. Moreover you will get updates and you will be able to uninstall it cleanly.

PS
If you don't find Azureus, you have to enable universe and multiverse repositories. Open System->Administration->Software properties and check the boxes which are not checked.[/QUOTE]

sorry but i don't find this a good answer. ("how i do x?" "do y instead")

i have the same problem. i had to install thunderbird manually because the one in the repository didn't work anymore. now it's in my ~/prg/ seeking for the right place...

---

### Post by Nonno Bassotto on 2006-07-05
Sorry if you don't thin this is a good answer. I thought that the original poster was coming from windows and didn't know how to install software in linux. In windows you are used to download software form some site and then install some exe, in linux this is not the way to go.
Clearly not everything is in the repos, so OCCASIONALLY you will have to install something manually. In this case the method varies from program to program, but usually you will have a precompiled deb package (in which case you can just double-click it) or you will have the source to compile.
In the case of thunderbird, I didn't install it, but there's a file called mozilla-installer-bin,so I'd try to run it. Extract the files, say in ~/thunderbird, and then opena terminal and write
```

cd thunderbird
sudo ./mozilla-installer-bin

```
Anyway, what is the problem with the version in the repos? A lot of people here use thunderbird, so if you search the forums you will probably find out how to solve your problem.

---

### Post by lepre on 2006-07-05
[QUOTE=Nonno Bassotto]
Anyway, what is the problem with the version in the repos? A lot of people here use thunderbird, so if you search the forums you will probably find out how to solve your problem.[/QUOTE]

i opened a [thread]("http://ubuntuforums.org/showthread.php?t=198504") about it. and a few had my same problem, but no one was able to say how to use the one in the repos again.

anyway i found that manually installed app should go in /usr/local :KS

---

