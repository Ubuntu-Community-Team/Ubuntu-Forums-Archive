---
title: "bash: /etc/apt/sources.list: Permission denied"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by MissNails on 2012-10-17
So..... I'm sort of new to Ubuntu (I think I have Precise Pangolin installed (12.04)) , and I've recently moved out of the United States to the UAE. Lately, I've been wanting to have more privacy in this dictatorship country and tried to download gpa (some application for the GNU Privacy Guard) but when I use the command:

sudo apt-get install gpa

 All I get is this: E: Unable to locate package gpa

 So, then I decided to try to add the software from the "Universe" repositories and typed: /etc/apt/sources.list

but I got this lovely message: bash: /etc/apt/sources.list: Permission denied. 

So, how can I install the [GNU Privacy Assistant]("http://www.gnupg.org/gpa.html") from the Universe repository? 

Thanks!

---

### Post by SlugSlug on 2012-10-17
gksudo gedit /etc/apt/sources.list

Also pretty sure you can enable that repo in Ubuntu Software Center or what ever its called

---

### Post by Lars Noodén on 2012-10-17
/etc/apt/sources.list is a file to edit rather than a program to run.  At this early stage it might be better to work with it via the Software Center or Synaptic.  You can find details in the community documentation about adding a repository:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you use Thunderbird, you might be interested in the add-on Enigmail which uses PGP/GPG on your mail.

KDE also has a nice front end for gpg, called kgpg.

---

### Post by drmrgd on 2012-10-17
Looks like GPA is only available for older versions of Ubuntu.  Looking around for a minute, though, I found a Forum Post suggesting that you could either install an GPA from source (and there is a warning about newer versions causing some problems), or use Geany instead.  I think going the Geany route might be a little better:

[http://ubuntuforums.org/showthread.php?t=2010229](http://ubuntuforums.org/showthread.php?t=2010229)

Also, I should point out that you can't edit /etc/apt/sources.list as you've tried.  It's actually a text file that lists the repositories to search for software.  If you wanted to add a repository to it, you can manuall edit the file by using:

```
sudo nano /etc/apt/sources.list # or replace 'nano' with a more preferred text editor
```

or you can use the 'add-apt-repository' command:

```
sudo add-apt-repository ppa:<ppa_name>
```

Note that these are all administrative tasks, and so you need 'sudo' to perform them, which grants admin level permissions for the task at hand.

---

### Post by Lars Noodén on 2012-10-17
When using nano with a configuration file, it can be a good idea to invoke it with [-w](http://manpages.ubuntu.com/manpages/precise/en/man1/nano.1.html) so that long lines do not get wrapped.  

```
sudo nano -w /etc/apt/sources.list
```

Getting an unwanted line break in the middle of a configuration can cause trouble.  Some of the lines in sources.list will be over 80 characters in length and are at risk for getting wrapped.

---

### Post by drmrgd on 2012-10-17
> **Lars Noodén said:**
> When using nano with a configuration file, it can be a good idea to invoke it with [-w](http://manpages.ubuntu.com/manpages/precise/en/man1/nano.1.html) so that long lines do not get wrapped.  

```
sudo nano -w /etc/apt/sources.list
```

Getting an unwanted line break in the middle of a configuration can cause trouble.  Some of the lines in sources.list will be over 80 characters in length and are at risk for getting wrapped.

Very good point!  I forgot about that as I have it pre-defined in my .nanorc file.  Good thinking!

---

