---
title: "Setting PATH variable...some confusion"
date: 2018-10-02
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2018-10-02
Hi
Simply trying to install YTini
[http://yt-project.org/#getyt](http://yt-project.org/#getyt)

After installing am told to edit my PATH variable.

But after some googling it seems there are a few ways to do this

1) From the command line
> $ export PATH=/home/jim/02_Scripts/ytini/yt-conda/bin:$PATH 

2) by editing /etc/environment
> /usr/bin/sudo -H gedit /etc/environment

Confused I tried both methods.
Now when I do 
> $ echo $PATH

I see
> /home/jim/bin:/home/jim/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/jim/02_Scripts/ytini/yt-conda/bin:/snap/bin


And if I open /etc/environment I see
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/jim/02_Scripts/ytini/yt-conda/bin"


Can anyone please explain what is happening and if my $PATH is correctly set?

---

### Post by TheFu on 2018-10-03
I've never touched the /etc/environment  when I only want to modify 1 userid's PATH.  Don't tough entire system settings for a single userid's needs.

Where a PATH should be updated completely depends on the shell being used. tcsh gets handled differently than Bourne Shell which is different from Bash or zsh or fish.

There is a default PATH, so you need to NOT screw that up.  When you modify it, don't replace it.  Either append or prepend your update to it. There are a few different ways to make a PATH active.  For now, until you understand more, just logout and login again.  No need to reboot.

Let's assume you are using bash for the shell. I always want my ~/bin/ in my path - prepended.
Add this to the bottom of my ~/.bashrc file:
```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
     export PATH="$HOME/bin:$PATH"
fi
```
If I'm doing something fancy in a script that might be called more than once per login, I might check whether that path was already added to the PATH environment variable.

Clear enough?

And please use **sudoedit** instead of sudo gedit to modify system files.  Just set the EDITOR environment variable in ~/.bashrc to use gedit, if that is what you prefer. OTOH, gedit doesn't work on Ubuntu Server or any router.  ```
export EDITOR=gedit
```

---

### Post by Dennis N on 2018-10-03
In (at least) Ubuntu 18.04, if you have an existing folder **~/bin**, then the script in **~/.profile** already has code to add **~/bin** as the first location in $PATH. If **~/.local/bin** exists, it will add that to $PATH too.

---

