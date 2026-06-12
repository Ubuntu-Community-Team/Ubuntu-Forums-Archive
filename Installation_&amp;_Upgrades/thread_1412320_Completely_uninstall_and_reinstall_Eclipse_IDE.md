---
title: "Completely uninstall and reinstall Eclipse IDE"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by schworak on 2010-02-21
I am VERY NEW to Ubuntu and have only limited experience with Linux in general. (mostly command line for web dev)


I started using Eclipse a few days ago and today something went wrong. I can no longer create a project for Java. I have tried several times to uninstall and reinstall but nothing seems to fix the problem.

The question is, how do I completely uinstall Eclipse so there are no bones left around and then do a full reinstall so I can start creating Java packages again? I am just learning Eclipse so keep your instructions simple please. Thanks so much!

---

### Post by MelDJ on 2010-02-21
to completely remove it, go to system-admin-synaptic package manager.
then search for the eclipse package and right click it and select "mark for complete removal"
then press apply to let the uninstall process start.
after it has finished, right click the package and press mark for installation and press apply to reinstall

---

### Post by tito_drum on 2011-05-16
Hey,
I had huge problems trying to reinstall eclipse because when I updated from last ubuntu version to the new one all the privileges changed and I had to do every thing as a root. Also I had big troubles with the plug-ins because they were there but eclipse didn't showed them. so here is what I did to start a clean reinstall.
1. First log in as a root $su - root
2. $apt-get autoremove eclipse
3. $rm -r /usr/lib/eclipse (will remove all the plugins that were lost or were giving you problems and also configuration files which if you are new with eclipse for sure there is nothing to keep)
4. $apt-get install eclipse
5. $eclipse (launch eclipse)
6. add all the plugins you want from a clean instalation

I'm sure there must be a cleaner way but this one after 10 thousand attempts was the only one that gave me a sweet result.

After doing all of this, exit root and launch eclipse as a regular user.

---

### Post by IWantFroyo on 2011-05-16
```

# sudo apt-get remove --purge eclipse
```
At least I think that's it...

If you're just programming Java, you should try Geany.
I use Geany for my Java, DreamPie for Python, and NetBeans for Java GUI stuff (although I don't do that much).

---

### Post by tito_drum on 2011-05-17
> **IWantFroyo said:**
> ```

# sudo apt-get remove --purge eclipse
```
At least I think that's it...

If you're just programming Java, you should try Geany.
I use Geany for my Java, DreamPie for Python, and NetBeans for Java GUI stuff (although I don't do that much).

I tried that one but I got same problem. Plugins and features and configuration files weren't deleted. So that's why I recommend to delete manually those files. It looks like there is a bug related.

---

### Post by Themotorman on 2012-05-26
I tried all of above suggestions but there are still bits of Eclipse around.
I tried tio follow "Programming Android" where the authors say do NOT install via Ubuntu repositories. I am new to this and need a working version of Eclipse . I would like to try starting again but need a complete cleanup to do so. Can anyone give a newby the step by step code to do this, so I can reinstall a clean copy . I haven't yet done anything useful with eclipse so have nothing to lose, but I am concerned about dependencies that might be used in other prgms
thnks .

---

### Post by Bapun007 on 2012-05-26
Eclipse made a workspace file in your home directory(THAT CONTAINS YOUR PROJECTS ALSO) . Try to backup that file somewhere else and delete that folder . 

After that try to install eclipse from its official website , not from ubuntu repo . if everything works then you can open your old projects again.

---

### Post by lisati on 2012-05-26
Back to sleep, old thread.

---

