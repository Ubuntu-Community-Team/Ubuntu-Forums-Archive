---
title: "How to install themes"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by telcar on 2016-10-23
So in my searching i saw another post here about themes, so i apologize if this is in the wrong past. I'm just getting started with ubuntu 16.10 and normally i wouldn't worry about something as irrelevant as a theme but i am visually impaired. The standard white and bright themes hurt my eyes. I normally use the high contrast themes like in windows and there is a high contrast them already in ubuntu. The pre-installed one tho is black text on white, if i could invert that. that would be ok i guess. I downloaded a high contrast black theme here [https://www.gnome-look.org/content/show.php/?content=50077()](https://www.gnome-look.org/content/show.php/?content=50077()) and also this black GTK theme here([https://www.gnome-look.org/content/download.php?content=45829&id=1&tan=69257344](https://www.gnome-look.org/content/download.php?content=45829&id=1&tan=69257344)). I read on google i needed to creat a theme folder in the home dir and moved the extracted theme to the folder. I downloaded to different tweak tools but neither of the themes show up in either. I tried rebooting and all kinds of other crap but no success any help would be much appreciated, Thanks in advance.

---

### Post by vasa1 on 2016-10-23
> **telcar said:**
> ... 
ubuntu 16.10 
...
visually impaired.
...
downloaded a high contrast black theme here [https://www.gnome-look.org/content/show.php/?content=50077()](https://www.gnome-look.org/content/show.php/?content=50077()) and also this black GTK theme here([https://www.gnome-look.org/content/download.php?content=45829&id=1&tan=69257344](https://www.gnome-look.org/content/download.php?content=45829&id=1&tan=69257344)).
...
create a theme folder in the home dir 
...
**Re ubuntu 16.10:** Non-lts versions of any *buntu are okay for more experienced users or for explorers. If you want a more stable system, use 16.04 for its entire life unless you have a genuine need for newer software or your hardware works better with a non-lts version.

**Re. visually impaired:** I too do not like bright colors on my screen. See the attached image.

**Re. downloaded a high contrast black theme here:** unless you know what you're doing, getting a theme from outside the standard repos may not give you what you want. You at least need to check if the theme is compatible with your desktop environment. IOW, know your gtk version by running ```
dpkg -l libgtk2.0-0 libgtk-3-0
```and make sure your theme is written for that version. Also make sure the theme is "complete": compare the list of files provided by the downloaded theme with that of a default theme such as Ambiance or Radiance.

Also be aware that several new themes are "compiled" (for want of the correct technical term). They won't be easy to tweak. In other words if you want to change #fff to #555 somewhere, you'll need to know much more than how to use a text editor. A group of pretty trustworthy guys have come up with a tool to tweak several aspects of certain compiled Numix-based themes. This tool is not yet available in the standard repos, AFAIK. See [https://ubuntuforums.org/showthread.php?t=2322710](https://ubuntuforums.org/showthread.php?t=2322710) and [http://www.webupd8.org/2016/05/easily-create-your-own-numix-based-gtk.html](http://www.webupd8.org/2016/05/easily-create-your-own-numix-based-gtk.html) for more. So even if the default is bright and white, you get a nice GUI to make things dark and gloomy ;) 

BTW, if you're sufficiently obsessive, you may also want to hunt for (or learn to tweak) icons and window decorations which aren't controlled by the gtk theme (client-side decorations excluded).

**Re. create a theme folder in the home dir:** remember it should be a hidden folder, *~/.themes* and not *~/themes*.

---

