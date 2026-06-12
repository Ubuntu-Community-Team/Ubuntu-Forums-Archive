---
title: "Trouble with proxy and Update Manager"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by wilwil0 on 2010-05-03
First time poster here, hope I put this in the right section, sorry if it isn't.

I'm using 9.10 and trying to update to 10.04 using the Update Manager. Anyway my problem is to do with the proxy. Whenever I try to install any updates it comes up with:

>  W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-libs4+5_4.3.2-0ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-libs4+5_4.3.2-0ubuntu7.2_i386.deb)
  Could not resolve ‘[[name of proxy I used somewhere else]]’
I'm guessing it is to do with the proxy I used to use whenever I used the internet somewhere else. I have gone into System->Preferences->Network Proxy and changed the proxy settings to Direct Internet Connection. 

I have also gone into System->Administration->Synaptic Package Manager->Settings->Preferences->Network and changed it to Direct Internet Connection as well. Just in case.

I am running Ubuntu 9.10 on a Samsung NC10.

The internet is working fine on Firefox.

I hope that's enough information for you to identify what's still wrong with my Update Manager, if it isn't just ask what else you need to know/test on it and I'll do it.

If I were to update from a CD, would that erase all of the settings and thus solve my problem? Albeit erase all my data, I kind of want to avoid that.

---

### Post by lechien73 on 2010-05-03
When you open a terminal window and type "export", do you see a "http_proxy" variable in the list? If so, your proxy settings are probably still set in /etc/environment

Just type:

```
sudo gedit /etc/environment
```

and remove the proxy lines. You may have to restart before it takes effect everywhere.

Regards

---

### Post by wilwil0 on 2010-05-03
Hey l[echien73]("http://ubuntuforums.org/member.php?u=1031904")

I have typed in that export thing and it has come up with the proxy like you said.

I then typed in your next instruction, though I'm not sure what you mean by removing the proxy lines. What does that mean I have to do?

A new window called "Enviroment (etc)" has come up, though that is blank.

---

### Post by lechien73 on 2010-05-03
Ok, if the file is blank then it indicates that the proxy settings aren't being set through there. Please could you check the contents of your /etc/bash.bashrc file?

Thanks

---

### Post by sjerome1 on 2010-05-03
Hello, 

You could also try looking at the file /etc/apt/apt.conf, and verify that the proxy information has been removed, or if you need it, you may need to add your userid, and password in the form of username:passwd@proxy.mine.com:<port number>.

As a thought.

Regards.

---

### Post by wilwil0 on 2010-05-03
Hey, the file opens, not sure what I'm supposed to be looking for.

> # System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
    cat <<-EOF
    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.
    
    EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
    function command_not_found_handle {
            # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
           /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
        else
           return 127
        fi
    }
fi

That's the entire contents of the file, I've read it all and can't see any references to proxies or html so I'm not sure what I'm supposed to do or even be checking :confused:  sorry, bit of a newbie as you may have guessed.

---

### Post by wilwil0 on 2010-05-03
> **sjerome1 said:**
> Hello, 

You could also try looking at the file /etc/apt/apt.conf, and verify that the proxy information has been removed, or if you need it, you may need to add your userid, and password in the form of username:passwd@proxy.mine.com:<port number>.

As a thought.

Regards.

I looked in that file and there was proxy information. I deleted and saved the changes but the problem persits. Do I have to restart it first? I any case I can try altering that info at the place I need to use a proxy, so that information has come in use anyway :).

I'm guessing you meant : P without the space and not :P ?

---

### Post by wilwil0 on 2010-05-03
Just an update (sorry for the double post)

Restarted it, still not working :(

Checked the files again, still blank and no proxies, anywhere else proxy settings could be interfering with the updating process?

---

### Post by wilwil0 on 2010-05-09
After I changed those things I could download things off of the Ubuntu Software Centre whereas I couldn't before, that mean anything?

---

