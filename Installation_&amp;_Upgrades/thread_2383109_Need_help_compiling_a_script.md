---
title: "Need help compiling a script"
date: 2018-01-21
forum: Installation &amp; Upgrades
---

### Post by warmango on 2018-01-21
I simply need help compiling a script that i can run on my server so i can install a lot of stuff i use at once. In the order in which i post it

 i need it to add the following code to my home Directory in the file ".bash_aliases"
```
alias upgradeALL='sudo apt update && sudo apt upgrade'alias Dlocalhost_0='export DISPLAY=localhost:0'
alias Dlocalhost_1='export DISPLAY=localhost:1'
alias Dlocalhost_2='export DISPLAY=localhost:2'
alias AliasN='source ~/.bash_aliases'
alias C_DRIVE='cd /mnt/c'
alias nano-alias='nano ~/.bash_aliases'
```

i also need to add the following code to
/etc/init.d 
as a standalone file, like "custom.sh"
```
exec "scource ~/.bash_aliases"

```

then it to run this command, although this can be a separate SH file also
```
exec "sudo dpkg -i ~/OPENBOX.deb"
exec "sudo reboot"
```


If you have any help, please offer it

---

### Post by TheFu on 2018-01-21
I don't think you want to "compile" anything. That is a specific term for converting a compiled language into machine code.  Just use normal scripts.

Or, since you are doing mostly setup things, why not reuse a tool designed specifically for this - that's what DevOps is about.  Ansible would be the tool I recommend, but you have to know how to do everything manually first. It isn't some magic wand.

And looking at the post above, there are many details incorrect, which will cause your script to fail.  I'd also question installing anything directly from a .deb file, unless you have a really, really, really, good reason.  openbox is available in the repos, for example.  Security fixes will be backported to the repo version, which you probably want.  Using repos and PPAs is THE REASON, many people prefer Linux over other OSes.  Patching isn't just for the OS, but for all programs running on it, but only if repos from respectable sources are used.

For some just starting out learning to create a script, it is just to put the same commands you type into the shell into a file and running that file.  So, how would you do each of the steps listed above from a terminal?  
[https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html) is a guide written for beginners.

But ... if you will be doing this a bunch, but for less than 500 systems, I'd really look into Ansible.

---

### Post by warmango on 2018-01-21
I will look into that, I was using a command that copies what I put into the quotations into a designated file, 

It will only be used on 2-3 machines, 
I will look at ansible when I have the time,

Also can you tell me what would cause the script to fail? I'm new to making scripts on my own

---

