---
title: "Unable to install Samba ubuntu update"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by yolloms on 2007-02-16
I hit the small undata icon from the tool bar to install a few updates that are available.

It pops up saying cannot uninstall/install software. open synaptic.

So i open synaptic and it says 1samba package is broken use broken filter to locate it.

So i do that, its samba     3.0.22-lubuntu3.2

i click repair broken packages and then click apply.

it starts downlaoding and when it tries to install i get this message

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb: 
subprocess new pre-removal script returned error exit status 102

i even tried #sudo apt-get install -f
to no avail.

any ideas what i should do.:confused:

---

### Post by jpkotta on 2007-02-16
I experienced this too.  It was complaining about a symlink to an init script.  I did a ```
sudo update-rc.d samba remove
``` to delete the link (you can also delete it by hand with rm).  I still don't think samba is installed correctly though, but I'm not sure because I'm not using it at the moment.

---

### Post by iggyboy on 2007-02-17
I'm having the same problem for about last 2 weeks, and it's very annoying cos' I can't do any update or installation for other programs. Synaptic Package Manager always ask to fix broken package with no success.

> sudo update-rc.d samba remove
the above code did not help but return with "not removing" error!

Can somebody give some tips... please.

ThankX :)

---

### Post by yolloms on 2007-02-18
it keeps saying use -f for me

i try using

```
 sudo update -f
```

any more ideas???

---

### Post by picker77 on 2007-02-18
I'm having exactly the same problem - see my post of 10 hours ago. Hoping for a solution soon.

---

### Post by elraun on 2007-02-18
check to see if apt is complaining about a broken symlink to samba.

if it is, you can remove it.

# sudo cd /etc/rc2.d

# ls -l 

you should see the broken link. rm it.

create a new link to the proper file, something like:

# sudo ln -s /etc/init.d/samba S91samba (this part can vary for you)

then run:

# sudo apt-get -f install

you should now be able to update your system.

---

### Post by Peacepunk on 2007-02-21
A **Point'N'Click** option, to find the dead link & *sort the issue once for all*, is:

Open Terminal *(just once! Rest is Point-Click, period!)* && type:

```
sudo nautilus
``` - enter password for sure.

You now have a Power User Nautilus, **[SIZE="2"]beware of what you're doing![/SIZE]**

Use the search tool, keyword "samba" in your etc file,
[COLOR="DimGray"][see bottom if you end up with no matches, search tool in Nautilus is, huh,...][/COLOR]
it will return you with several, look for _ONE_CAPITAL_LETTER_,_TWO_NUMBERS_samba, most probably cramped by warning signs "root", "broken" & others.

(My system, I dig two, in folders rc2.d & rc3.d, called **K09samba**

Delete them, then have synaptic doing his update job again. Should be OK now, or at least return you another error code than** 102**

Do a search again, to be sure new symlinks where created. 
On my system, I have 7** (!)**:  **three**, called K19samba, in rc0.d >> rc2.d & **Four** from rc2.d >> rc5.d, called K20samba.

I think that should be* Foolproofed*. Close *Nautilus* _as sson as you finish_, this PowerUser mode allows for too much** accidental damage**!

It worked for me straight, I got my Samba Shares available && synaptic's nose rubbed :) stopped crying !

*SideNoteForDummies*: the Search Tool in Dapper* isn't* straightforward.

- Click "Search", upper-right toolbar of Nautilus, still in Power User Mode for sure.
- Write Samba in the text field
- Hit enter, it'll look in the root folder. Silly.
- Hit the second drop down box, should be called "root" because you are runing Nautilus as SuperUser, choose "**other**" (lower-most entry), go for **File System**, then** etc**, 
- hit **OPEN**
- Click on "**Refresh**" (Not sure, called *"actualiser"* in french), the button next to the **[SIZE="3"][COLOR="Blue"]+[/COLOR][/SIZE]** sign.

[SIZE="3"][COLOR="DarkRed"]Cheers.[/COLOR][/SIZE]

PS: being confused by the following
> 
elraun
sudo ln -s /etc/init.d/samba S91samba (this part can vary for you)

&& not having found the broken link in the Terminal, I used the above method to get rid of the issue:*[SIZE="2"] Thanks to fellow posters[/SIZE]* but felt that where I fail, well, some others may as well, be as dumb as I am, you never know,...

---

### Post by vivaporu on 2007-04-04
peacepunk 

thank you so freaking much i've had this problem for over a month and had gone from 
living with it,smacking my wife (joke people) to considering changing distros, you don't know how much you saved me i was about to go buy vista (joke people) i figured it was somehting like your how to stated i just didn't know what to delete, being the noob that i am.as far as i'm concerned your that best thing since sliced bread keep up the good work.

---

### Post by Peacepunk on 2007-04-04
It'll just make us TWO dumb users.

Keep on these forums - so, ubuntu for that matter, they are the greatest ressource in the Linux world.

And I tried some, I can tell.

Cheers, thanks for the Thanks.

Peacepunk

---

