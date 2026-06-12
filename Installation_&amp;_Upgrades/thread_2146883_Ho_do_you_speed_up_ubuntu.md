---
title: "Ho do you speed up ubuntu"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2013-05-20
Hello in there this is Chris:)
 I already have ubuntu 12.04 LTS working just fine but I would like to speed it up a bit. I have watched a video on Youtube which gives a few tips to turn off some start up apps you feel are not absolutely vital. 
Here is the line of command they give you to display all the applications on start up when you launch ubuntu:

sudo sed i- "/NoDisplay=true/NoDisplay=false/g"/etc/xdg/autostart/*.desktop
sudo password for XXXX :

[B]And here is what I get each time I type the above in the terminal:
[/B]

Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  --follow-symlinks
                 follow symlinks when processing in place
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if extension supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -r, --regexp-extended
                 use extended regular expressions in the script.
  -s, --separate
                 consider files as separate rather than as a single continuous
                 long stream.
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
      --help     display this help and exit
      --version  output version information and exit

If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.

GNU sed home page: <http://www.gnu.org/software/sed/>.
General help using GNU software: <http://www.gnu.org/gethelp/>.
christophe@christophe-TPS01:~$ 

Thank you in advance for answering this.

---

### Post by SlugSlug on 2013-05-20
Is it not fast enough??

If it ain't broke don't fix it.

That being said if you still want to mess about your hyphen was the wrong way

sudo sed i-
should be 
sudo sed -i

---

### Post by christon74 on 2013-05-20
Thanks. Solved.

---

### Post by christon74 on 2013-05-20
There are some apps I have never needed and never used like Ubuntu-One and Bluetooth.

---

### Post by christon74 on 2013-05-20
This thread is now solved /solved/ solved/solved.

---

### Post by mastablasta on 2013-05-20
> **christon74 said:**
> There are some apps I have never needed and never used like Ubuntu-One and Bluetooth.

just because they are on the disk it doesn't mean they are slowing the operating system they are onyl taking disk space. and they take a very small part of disk space...

---

### Post by vasa1 on 2013-05-20
> **mastablasta said:**
> just because they are on the disk it doesn't mean they are slowing the operating system they are onyl taking disk space. and they take a very small part of disk space...
I think OP is concerned about "start up" time, not disk space.

---

### Post by claracc on 2013-05-20
> **christon74 said:**
> This thread is now solved /solved/ solved/solved.

You have to mark the thread as solved in the following way: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bucky Ball on 2013-05-20
> **claracc said:**
> You have to mark the thread as solved in the following way: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Done, done, and done, but yes, that is how you do it. ;)

---

### Post by oldos2er on 2013-05-20
> **christon74 said:**
>  I have watched a video on Youtube which gives a few tips to turn off some start up apps you feel are not absolutely vital. 

Can you give a link to this video?

---

