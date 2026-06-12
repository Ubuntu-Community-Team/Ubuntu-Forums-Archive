---
title: "Update Manger Error"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by notslony on 2011-03-05
I Got This Error Today So Ubuntu Said To Update You WIll Need To Go To System> Administrator>Update Manger But When I Open it It Give Me A Error  

'E:Type 'PulseAudio' is not known on line 42 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I Need Help Because i Like Trying Out New Ubuntu Versions 
Im Using Ubuntu 10.04 Trying To Upgrade To 10.10

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)
I Need Help:(

---

### Post by minigeek on 2011-03-05
> **notslony said:**
> I Got This Error Today So Ubuntu Said To Update You WIll Need To Go To System> Administrator>Update Manger But When I Open it It Give Me A Error  

Ubuntu Error E:Type 'Pulseaudio' is not known i line 54 in source list /etc/apt/sources.list,The List Sources Cant Read

I Need Help Because i Like Trying Out New Ubuntu Versions 
Im Using Ubuntu 10.04 Trying To Upgrade To 10.10

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)
I Need Help:(

Hi

Try this 

1- sudo vi +54 /etc/apt/sources.list
   This will open the file at the line that has the error
2- Place a # at the beginning of the the line.
3- Save and exit the file.
4- Run Update Manager again

---

### Post by notslony on 2011-03-05
> **minigeek said:**
> Hi

Try this 

1- sudo vi +54 /etc/apt/sources.list
   This will open the file at the line that has the error
2- Place a # at the beginning of the the line.
3- Save and exit the file.
4- Run Update Manager again

it Did Not Work in Terminal It Showed This 



E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Sat Mar  5 17:18:29 2011
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: ricky-desktop
        process ID: 3343
While opening file "/etc/apt/sources.list"
             dated: Sat Mar  5 16:17:27 2011

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.
"/etc/apt/sources.list" 57 lines, 3218 characters

What Do I Do With That

---

