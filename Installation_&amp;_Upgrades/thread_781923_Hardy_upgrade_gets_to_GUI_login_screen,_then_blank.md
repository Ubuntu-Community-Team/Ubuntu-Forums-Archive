---
title: "Hardy upgrade gets to GUI login screen, then blank and returns to login"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by fixitdude on 2008-05-04
On upgrading from Gutsy to Hardy I could get to the log in GUI screen, mouse working and all that but then when I logged in it would show a black screen and then after a little wait return to the log in screen again. (black screen is where X is restarting under the new user, X was working at that point because I had a GUI)

This may also apply if you have your system set to automatically log in a user, then it would just keep retrying and you see nothing but a blank screen most likely.

After hours of work on this, here's the solution.

I moved all the ".font" files (from my users home dir) into a new directory (effectively removing them).

(Press ctrl-alt-F3 to get to console, log in as user)
mkdir oldfonts
mv .font* oldfonts/

How I found out is I created a new user and when I logged into that a new KDE started, asking me all the default questions etc. After that I had to figure out what was different from a new user and my old user. A new account didn't have the ".font" files. But of course I figured that out last.

Point is, IF YOU ARE HAVING PROBLEMS, try creating a new user to see if it works then work in "reverse" to figure what the differences are.

(from root, if you wanted to try this new user thing)
mkuser newusername

The logs showed things like "ksplash" and a couple others were segfaulting. 
Really stupid, they should just say bad format in ".font" file or something. Talk about throwing you off the trail.

tail -500 /var/log/messages | less

But I tried a lot of other stuff people suggested here first, so possibly 
something else helped me get to this point, so I will post some of the other stuff that probably won't hurt to do.

Don't forget to make sure you have room left on your HD.
df

Make sure you are upgraded completely on kde
apt-get install kde

If you are using kubuntu, this may help
sudo aptitude install kubuntu-desktop

I didn't use this one but it may help you get X running.
sudo dpkg-reconfigure -phigh xserver-xorg

By the way, this command "sudo update-manager --dist-upgrade" doesn't work if you can't get X to work.

Another error in the log was for "run_parts", so I edited /etc/X11/xorg.conf

Replace line:
RESOURCEFILES=$(run_parts $SYSRESOURCES)

with
RESOURCEFILES=$(run-parts $SYSRESOURCES)

Notice the underscore is changed to "-", this is a known debian bug.

And a side note, for those who tried to switch to "xdm" you can run this
sudo apt-get install --reinstall gdm
---- or ----
sudo apt-get install --reinstall kdm

To get it to ask you which one you want to start with (kdm for the default 
ubuntu style login screen).

Hope this saves you some time. Cost me a whole day. (I may post this in more than one thread, sorry in advance)

---

### Post by umberleigh on 2008-05-07
I had a similar problem after upgrading to Hardy Heron and installing KDE 4.

I could log in, but KDE 3.5 would display with no window decorations/borders, and KDE 4 would log in, but just give me a blank grey screen and a mouse cursor.

I found the quickest solution was this:

First, open up a terminal and login as yourself, then backup your dot files (config files
```

su YOUR_NAME
cd ~/
mkdir old_dotfiles
mv ./.* old_dotfiles
```After this you should be able to logout/restart X and login with your account.

Then you can copy back config files (for me .purple, .gaim, .mozilla and .kde/share/apps/ktorrent were the most important) one by one, checking each time that if you restart X (Ctrl-Alt-Backspace) you can still log in and that everything works, or alternatively reconfigure KDE and your applications manually.

Edit:
I later found the Compiz Fusion desktop effects were causing these issues. It can be sorted by searching for any folders/files in your home directory containing the phrase *compiz* and deleting them

---

### Post by alexmclaren on 2008-07-04
I have this problem on Hardy Heron but am not running KDE on top of that, will this work anyway?

---

