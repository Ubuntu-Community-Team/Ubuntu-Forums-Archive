---
title: "A problem occurred when checking for the updates"
date: 2023-10-01
forum: Installation &amp; Upgrades
---

### Post by juanbuntu on 2023-10-01
OS = Linux Ubuntu 22.04 LTS, running on AMD Ryzen CPU with 24GB of RAM, nVidia GE 1060  GPU Card.

I was trying to upgrade python3 from 3.10 to 3.11.5. I followed the instructions from the python site, which instructed me to issue a cmd like "pip3 install python 3.11".
After that I tried to open the gNome terminal, which failed because there is a script at /usr/bin/gnome-terminal which in its first line has  a cmd "!/usr/bin/python" that I changed to "!/usr/bin/python3.11"

After that gnome-terminal still could not open, because there was a circular import /usr/lib/python3/dist-packages/gi..." so I tried to remove python3, and that crashed ubuntu.

After trying several times to reboot, issue apt-update, upgrade, etc, I still get an icon in the top left part of the screen, that looks like a stop sign, and that has the message "A problem occurred when checking for the updates".

It appears that the OS is not able to continue with the booting process (only one of the three monitors is active) and I am lost on how to move forward.
I would be grateful for any the help I could get to solve this  issue.

Thank you

---

### Post by ubfan1 on 2023-10-01
How did you "remove" python3?  Hopefully, you just removed the link /usr/bin/python3, not any actual python3.10 packages.

---

### Post by MAFoElffen on 2023-10-02
This from my file:
```

mafoelffen@Mikes-B460M:/data/ISO$ awk '/python/ {print $0 ;exit}' /usr/bin/gnome-terminal
#!/usr/bin/python3

```
@ubfan1  -- That file is a script, not a symlink... I think i understand what he said he did.

What happens if you boot from a Desktop I installation LiveUSB, mount the drive to /mnt... Then do
```

sudo sed -i '0,{s/python3\.11/python3/}' /mnt/usr/bin/gnome-terminal

```
That should only replaced the 1st match in the first line of that file...

When you do get this straightened out, read up on how to use 'pyenv' and 'virtualenv', so you can manage and run different versions of Python from a 'sandboxed' virtual environment. That is the way to do that safely.

You have just demonstrated how to break a system using a different version on the real system, which is very interdependent on Python Scripts and it's default installed version of Python3. Bad things happen when that gets cross-wired... 

Luckily you only changed that one line in that one file... and not something like removing anything or changing the update-alternatives. 

APT is big time dependent on Python. I know no-way to repair a system when APT breaks, besides having to do a full re-install and restoring the data and configs. And yes, I had been called in to trying to do that a time or much more. And had always ended the same.

---

