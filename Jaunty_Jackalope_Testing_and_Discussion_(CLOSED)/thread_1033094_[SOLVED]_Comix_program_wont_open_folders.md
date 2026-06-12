---
title: "[SOLVED] Comix program wont open folders"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-07
Recent update broke my comix programs ability to open folders.  Have to go to the file inside now.  Can someone else verify this with just a random folder of pictures if you don't have any real comics.

---

### Post by ShirishAg75 on 2009-01-07
Could you elaborate what issue you are having for I'm able to use comix just fine. Its able to browse directories and able to view .cbr and .cbz files just fine.

---

### Post by LordVeovis on 2009-01-07
> **ShirishAg75 said:**
> Could you elaborate what issue you are having for I'm able to use comix just fine. Its able to browse directories and able to view .cbr and .cbz files just fine.

If I open a folder directly (right click: Open with "Comix") it is as if I opened comix w/o specifying a target, as if I went to Applications >> Graphics >> Comix

Previously this worked, I saw a Comix update push through a few days back, didnt know if that was the cause or if I was anything I may have done.

---

### Post by ShirishAg75 on 2009-01-07
I tried what you say and was able to do it without an issue. 

Try the following.

```
$ rm -rf .comix
```

and then retry doing again with Comix. See if it reoccurs.

---

### Post by MaX on 2009-01-08
> **ShirishAg75 said:**
> I tried what you say and was able to do it without an issue. 

Try the following.

```
$ rm -rf .comix
```

and then retry doing again with Comix. See if it reoccurs.

Be aware that rm -rf .comix has to be done in your home folder or the folder of the user actually using Comix.

The command removes the config files for Comix so you'll have to specify new folders for where your comics' are stored etc.

---

### Post by LordVeovis on 2009-01-08
Thanks for the suggestion, but it didn't work.  I even went 1 step further to uninstall and reinstall comix.  No-go either.  Are you opening the folder directly and it works fine for the both of you?  Not files in the folder, but the folder itself?

---

### Post by HerrEkberg on 2009-01-08
As of Comix 4, support for opening directories directly was dropped (because I thought no one used it), but it has now been re-added. The changes are only in the SVN repository yet. You can check out the latest revision with:

```
svn co https://comix.svn.sourceforge.net/svnroot/comix/trunk comix
```

---

### Post by LordVeovis on 2009-01-08
> **HerrEkberg said:**
> As of Comix 4, support for opening directories directly was dropped (because I thought no one used it), but it has now been re-added. The changes are only in the SVN repository yet. You can check out the latest revision with:

```
svn co https://comix.svn.sourceforge.net/svnroot/comix/trunk comix
```

Thanks allot!  That's the main way I open comics.  I don't bother with compressing as it doesn't save much room as they are pictures.  That and I sometimes use comix to quick browse through pictures, not just comics.

EDIT: I ran the code that just checks.  How do I actually update to it?  Have not used SVNs in the past.

---

### Post by HerrEkberg on 2009-01-08
You can run it by simply executing src/comix.py, or you can install it using the install script. As an example, to install in /usr/local/, run:

```
sudo python install.py install
```

---

### Post by LordVeovis on 2009-01-08
> **HerrEkberg said:**
> You can run it by simply executing src/comix.py, or you can install it using the install script. As an example, to install in /usr/local/, run:

```
sudo python install.py install
```

Thanks allot!  I guess had I actually looked in the folder I would have seen a new folder >.<  Oh well.  I still may not have figured it out.  I mainly didnt know that running the svn command d/led anything.

Thanks again.

EDIT: As this is solved, so has it been marked!

---

