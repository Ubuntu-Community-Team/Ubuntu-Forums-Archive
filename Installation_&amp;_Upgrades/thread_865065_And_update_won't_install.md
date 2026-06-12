---
title: "And update won't install"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by Jim Lewis on 2008-07-20
I keep being told that "libnspr4-0d Netscape Port Runtime" is needed and available for installation, but when I try to install I always get an error message. 

This item originally was part of a LONG list of needed updates and patches.  All the rest installed OK.  This was left over and stays left over, but won't install.

Is it critical?  Is there some way to get it installed?  I'm using the latest version of Ubuntu.

---

### Post by bapoumba on 2008-07-20
This one ? [http://packages.ubuntu.com/hardy/libnspr4-0d]("http://packages.ubuntu.com/hardy/libnspr4-0d")

Please post your sources.list:
```
cat /etc/apt/sources.list
```

And the complete error to:
```
sudo apt-get update
```

---

### Post by Jim Lewis on 2008-07-20
I'm afraid I'm so new at this I don't understand.  I tried to install via the little sunburst icon at the top right on my screen.  That failed.  I went into Synaptic and tried again.  That failed, too.  

Yes the ones you show seem to be what I need, but I'm afraind I don't understand your references below.  I tried to drag and copy the error message(s) I got, but it wouldn't let me.  I dunno what you mean by "sources list."

My overall installation seems to be working just fine (I've been using UBUNTU for about 6 months now), but I'm sure there'll be a time wha I need this little bit that just will NOT install.

TNX for any help.

---

### Post by bapoumba on 2008-07-20
Please open a terminal (>Accessories >Terminal) and paste:
```
cat /etc/apt/sources.list
```
You can highlight the command and middle click to paste in the terminal. Paste back in a reply to this post the output of the command in the terminal.
(this command will list the content of the file)

Then paste:
```
sudo apt-get update
```
You will be prompted to enter your user password. Type it and hit return (nothing will appear on the screen, for security reasons. This command will read the sources.list file and check the repositories listed in the sources.list file for updates). Then highlight the complete output and paste it here too :)

---

### Post by Jim Lewis on 2008-07-24
MANY, many thanks.  That worked.

---

### Post by bapoumba on 2008-07-24
> **Jim Lewis said:**
> MANY, many thanks.  That worked.
You are welcome :)
I'm not sure what fixed it as these were just to be able to see where the problem was (probably the update), but anyway, congrats :)

---

