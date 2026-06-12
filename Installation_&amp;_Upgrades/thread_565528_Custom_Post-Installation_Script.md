---
title: "Custom Post-Installation Script"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by aaaantoine on 2007-10-02
For my next installation of Ubuntu, I am going to install / configure all the essentials by hand using the CLI.  What I will end up with is a text list of CLI commands that will make work what doesn't (e.g. wireless) and install all essential applications.

I would need to write a script that will go down the list of commands and execute each, one by one, as if it were in a command line.  If the command responds with an error (such as wget or apt-get install failing), the script would stop.  The script would perhaps receive a --continue argument to continue where it left off, or --repeat-last to repeat the failed command and continue from there.

Would Bash script be the best candidate for this?  Alternatively, does a script like this already exist?

---

### Post by kidders on 2007-10-03
Hi there,

Your idea seems interesting. Having thought about it for a few minutes, I would suggest dividing your post-install procedure into individual tasks, for example...[LIST]
[*]Configure something complicated ... wireless networking or Xorg, maybe.
[*]Fetch, compile & install a CVS version of something experimental ... compiz fusion, say.[/LIST]... well, you get the idea. Each task would be reasonably self-contained, and constructed with the possibility that it might be "resumed" in mind. Each one would then be expressed as a function. Since you mentioned Bash, what would you think of something like this? ...

```
#!/bin/bash

RESUME_LOG="/var/tmp/post_install"

# Figure out resume point
if [ -r "$RESUME_LOG" -a "$1" = '--resume' ]; then
    RESUME_POINT=`cat $RESUME_LOG`
else
    RESUME_POINT=0
fi

function perform_action {
    if [ ! $1 -lt $RESUME_POINT ]; then
        echo $1 > $RESUME_LOG
        action_$1
        if [ $? -ne 0 ]; then
            echo "Action $1 failed"
            exit 1
        fi
    fi
}

function action_1 {
    echo "Configuring networking"
}

function action_2 {
    echo "Installing something complicated"
    return 1
}

function action_3 {
    echo "Moving /home to its own disk partition"
}

function action_4 {
    echo "Rebooting"
}

mkdir -p `dirname $RESUME_LOG`
rm -f $RESUME_LOG

# #####################################
# Do some stuff
perform_action 1
perform_action 2
perform_action 3
perform_action 4
# #####################################

rm -f $RESUME_LOG
```Should something go wrong, invoking the script with "--resume" would restart the last task that failed to complete. The advantage in a task-oriented approach, rather than the individual command-oriented one you suggested could be illustrated as follows...[LIST=1]
[*]Command 1: wget http://somewhere.com/tarball.tar.gz
[*]The remote host truncates the file, or maybe returns a HTML document along the lines of "Service temporarily unavailable -- try again later".
[*]Command 2: tar xzf tarball.tar.gz
[*]This command fails, but resuming the script at this point won't correct the problem.[/LIST]Anyhow, this is just one idea that popped into my head. You might not like it.

---

### Post by maybeway36 on 2007-10-03
I have a simple (too simple?) /bin/sh script for post-install buisness. It installs all my programs and edits my config files with some perl trickiness I found on a web search.

---

### Post by aaaantoine on 2007-10-04
@kidders:  Neat idea.  I'll have to hang onto this thread.  Thanks!

When I install Gutsy final (or Hardy, depending how things go with Gutsy), I'll start playing around with this.

---

