---
title: "Blender Installation(s)"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by Robynsveil on 2012-02-19
Is it possible to have more than one version of Blender installed?

I've tried downloading from graphicall.org/unarchiving to folder/ navigate via terminal to blender file (would be called executable in Window, no idea what programs that run are called in Linux) and typing the name of the file - blender - at the prompt and it would bring up the installed via SPManager version of Blender.
So, I uninstalled that version via Synaptic Package Manager, and this time terminal tells me:
> bash: /usr/bin/blender: No such file or directory
No clue how to go from here. I tried the tips here:
[http://ubuntuforums.org/showthread.php?t=1527960&highlight=Blender](http://ubuntuforums.org/showthread.php?t=1527960&highlight=Blender)
but I must be something wrong, still. I would like to be able to run more than version of Blender.

Ubuntu 11.10, using Cinnamon desktop, 32 bit

---

### Post by Deepfriedice on 2012-02-20
I'm pretty sure you can only have one copy of a program *installed* at a time, but nothing should be stopping you from just having the executables for more than one version.

A thought: you said you are typing the name of the file you want to run, right?
When you type just an name into the terminal it tyies to run an installed program of that name, not the file.
To run a file called blender, you would need to type "./blender" (without the quotes)

I apologize If I'm assuming that you are doing something your not.

---

### Post by Robynsveil on 2012-02-20
Actually, no I didn't and thank you!

But even if I was in the folder (as in, I had navigated - cd - into that folder in terminal, it would still run the executable in some other setting. I've been trying to figure out where those settings are... I'm a total novice, all for having played with this OS for as long as I have. :redface:

---

### Post by Deepfriedice on 2012-02-20
What exactly do you mean by: > run the executable in some other settingIs some other copy of blender running instead of the one that you are trying to run?

Sorry for the confusion; your situation sounds pretty weird.

Also, I forgot to ask before, why are you trying to run blender from the command line rather than just double-clicking the executable file?

---

### Post by Robynsveil on 2012-02-21
I agree: that was horribly unclear.

In that other OS, I'm accustomed to having multiple versions of Blender available: just in case something isn't working correctly in one, I'll load the project in another.

In previous versions of Ubuntu, I could pretty much do the same thing: create a link to a specific version which would bring up that version. I would not have an actual Synaptic Package Manager-installed version, sinced the repositories are always notoriously behind.

Now, if I type blender in terminal, it apparently looks for a version of Blender that *was* installed (and now uninstalled) - to me that says some sort of path/file setting somewhere. I'm not very tech-savvy (clearly) but I have come to like terminal as really it make a lot of sense and is in a lot of ways faster than dialogues/wizards. Anyway, if I could be able to run whichever version of Blender I wanted (including experimental ones from Graphicall.org) that would be awesome. Any strategies you might have would be gratefully studied.

---

### Post by Robynsveil on 2012-02-22
Bit of a followup - I suddenly realised why I was using terminal to try to run Blender. I would navigate to the folder and double-click on blender and nothing happened. Then, I remembered: terminal gives you *reasons* why something doesn't run.
Voila la raison.

Which I did just now trying to run a g[raphicall.org build of Blender]("http://www.graphicall.org/817") - specifically for my system (32-bit) - featuring BMesh. Downloaded, un-archived, placed in my folder and tried double-clicking on the blender icon.

Nothing.

Navigated to it in terminal and ran it with:
```
myCoolSystem:~/blenderbmesh$ ./blender
```

which gave me:
> ./blender: error while loading shared libraries: libpython3.2mu.so.1.0: cannot open shared object file: No such file or directory

...which is informative. Clearly missing python 3 and/or libraries... gonna SPM that one...

---

### Post by Deepfriedice on 2012-02-22
I'm not sure what SPM is, but I am curious to see whether getting those libraries fixes this.

---

### Post by Robynsveil on 2012-02-23
> **Deepfriedice said:**
> I'm not sure what SPM is, but I am curious to see whether getting those libraries fixes this.

Sorry - SPM=*Synaptic Package Manager* ... searching in vain for these files. I'm pretty sure there's an easier (and more correct) way to resolve these dependency issues.

I did resolve the Python error problem, but now there's something not right with something else... now I get:

> ./blender: error while loading shared libraries: libopenjpeg.so.2: cannot open shared object file: No such file or directory

Oh, what a complex web... etc :)

---

### Post by ursaminor on 2012-03-06
Download the latest Blender 2.62 or from Graphicall. Place it in its own folder and place it in your Home file or wherever you like. You do not need to install it as it will work as a standalone program. After extracting you can click on the "blender" file and it will open up for you. You can even place Luxrender in the same file as Blender and follow the instructions per [http://www.luxrender.net/wiki/LuxBlend_2.5_installation_instructions]("http://www.luxrender.net/wiki/LuxBlend_2.5_installation_instructions").

---

