---
title: "Change Directory challenge/ Veeam installation"
date: 2024-07-02
forum: Installation &amp; Upgrades
---

### Post by vliscony2023 on 2024-07-02
I am trying to install veeam, and it asks me to instal from within its directory

my veeam directory is under home

but I can't seem to get to it.

cd /home gets me to home

and I can see the veeam directory under home

but I have not figured out how to get into the veeam directory.

---

### Post by currentshaft on 2024-07-02
What is "it"? Can you provide a reference for what documentation, message or error you're following?

Most of us likely have no idea what Veeam is. Help us out by describing what problem you're trying to solve with it.

---

### Post by grahammechanical on 2024-07-02
When the terminal opens it opens in the /home/username directory.

```
ls
```

will list the directories in /home/username. Assuming veeam or Veeam is the directory name

```
cd veeam
```

or

```
cd Veeam
```

should get in that applications directory.

Regards

---

### Post by TheFu on 2024-07-03
> **vliscony2023 said:**
> 
cd /home gets me to home

On Unix-like OSes, the "HOME" directory is the location spelled out in the passwd DB.  When you open a new terminal window, you will be in the current userid's HOME.

Veeam is a backup tool for VMware ESXi systems.  I used it at one client a long time ago, before they dropped VMware completely.  What I recall was that it cost $1000, didn't support incremental backups and since every VM backup was a full, we couldn't keep very many versions of the backups for each VM.  After we moved that client to KVM/QEMU, we also switched them over to a F/LOSS backup tool that ran much, much, much, faster after the initial backup was taken and was space efficient enough to retain over a year of daily, versioned, backups.  BTW, we knew those backup were good, because we tested the restores into completely new hardware and new VMs.  As an example, I backup about 15 VMs here nightly and the **total time for those to complete** with the F/LOSS tool is under 30 minutes.

There are many synonyms for this special directory. ~, ~/, ~username, $HOME are all the same, if the username matches the current userid.
To see your current directory, there is a command 'pwd' - present working directory.  Often, a shell program will maintain an environment variable with this too - $CWD - that's current working directory.  All Unix-like OSes work this way.

There is confusion between /home and ~/ because Linux has chosen to place all local users HOME directories under /home/ ... except the root userid, which is put under /root/.  There are historical reasons for this.

So .... root's HOME is /root/.  If you look at the passwd DB, you can see this.
```
$ getent passwd root
```

Use the **getent** tool rather than just looking inside the /etc/passwd text file for this information.  **getent** will use any configured networked, user DB to provide the information, not just look in a single, local, file.  On systems with thousands of users, it is likely that centralized user management with either NIS+ or LDAP will be used and only daemons and root will be local.

It should also be clear that using /home as the location for user's HOME directories isn't mandated.  Nearly everywhere I've worked the last 30 yrs, we specifically did NOT use /home/ as the location for user's HOME directories, since most of their data was stored on NFS storage and mounted only as needed.  Different sites would have different standards, but it was common to see /u/u1/albert4323 like HOME directories.  As more and more user's were added, more and more NFS storage would become available to hold their HOME's.  This is why having ~albert4323/ is handy.  It also explains how so many Linux home users never learn these things.  If you don't work in a large site, you'll likely never see NFS and need to have users HOMEs spread across many different disks.

You may have noted that I tried to use "HOME" when talking about the idea of a user's HOME directory and only used /home/ when talking about a specific directory.  If you re-read the instructions, you may see that they did the same thing and you missed that subtle clue.

Anyway, hope this is helpful in some way.  Step away from MS-Windows some more and all this will become clearer.  BTW, MS-Windows works exactly the same with directories.  We can even use the / as the directory separator.  Try it.   In a cmd.exe window, try **cd c:/windows**  It will work.  Cross-platform programmers have been doing this for many decades. Unix, Linux, MacOS, and MS-Windows ... all use exactly the same hierarchy for directory systems.  Sure, the specifics of which directories hold what and which can be mounted read-only are different, but moving around in them all is the same.

---

### Post by vliscony2023 on 2024-07-03
here is some experimentation

quote
rogier@rogier-HP-Z4-G5-Workstation:~$ cd veeam
bash: cd: veeam: No such file or directory
rogier@rogier-HP-Z4-G5-Workstation:~$ cd /veeam
bash: cd: /veeam: No such file or directory
rogier@rogier-HP-Z4-G5-Workstation:~$ cd /home
rogier@rogier-HP-Z4-G5-Workstation:/home$ getent passwd root
root:x:0:0:root:/root:/bin/bash
rogier@rogier-HP-Z4-G5-Workstation:/home$ 


unquote

Bottom line, I see the veeam directory under home, logically after a directory called "Templates",

But I still can not navigate to it in order to installe that program from within that directory as it asks me to

see instruction:

quote
[h=1]Connecting to Veeam Software Repository[/h]
[COLOR=#232323][FONT=&quot][COLOR=var(--base-font-color,#232323)][FONT=inherit]To install Veeam Agent for Linux on a Linux computer, you must first connect the computer to the Veeam software repository. The Veeam software repository contains the Veeam Agent installation packages specific to the Linux distribution, version and architecture of the computer where you plan to install the product.[/FONT][/COLOR]
[COLOR=var(--base-font-color,#232323)][FONT=inherit]To connect to the Veeam software repository, do the following:[/FONT][/COLOR]

[LIST]
[*]Download the Veeam software repository installation package ([FONT=&quot]veeam-release[/FONT]) from the [this Veeam webpage]("https://www.veeam.com/linux-backup-download.html"), and save the downloaded package on the computer.
[/LIST]

[LIST]
[*]Navigate to the directory where you have saved the [FONT=&quot]veeam-release[/FONT] package and install the package using the command for your Linux distribution.
[/LIST]
[/FONT][/COLOR]
unquote


and I am still stuck unable to navigate to the veeam directory and feeling stupid ;-)

---

### Post by TheFu on 2024-07-03
I hate to say this, but it is clear that you don't understand how to use the 'cd' command, nor how to access directories with either relative nor absolute paths.  Whoever provided your Unix/Linux training needs to be visited and you need to demand your money back, ff you were given a passing grade.

Until you learn those things, you will struggle to do anything on Unix-like OSes.

[https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) is a free, no hassle, book that will explain all the basics, including this stuff. Please take the time to learn it.  It is in chapter 2 (5th Ed.), which shows how basic this understanding is.  

When I taught beginning Linux at the local University, we used an edition of that book, but absolutely **any** beginning Unix/UNIX/Linux book would cover what you need to learn.

---

### Post by vliscony2023 on 2024-07-04
Well thanks for that great book reference.

My linux skills are fairly rudimentary, but used to be better. It will come back to me, but I appreciate th ehandholding.

What is frustrating is that at one time I could do thiis in my sleep, but at this point I seem very rusty. 

I had Linux on a computer since version 0.90, and at one point was mderately handy with it, but I am getting this book. 

Meanwhile continue to hope someone gives me a pointer about where I am stuck.

---

### Post by aljames2 on 2024-07-05
When I pull up my copy of the Linux commands book (pdf), pages 7-12 (chapter 2), covers navigating directories and includes using important commands like (pwd and ls). It explains the concepts of absolute paths & relative paths.

I am not entirely sure you know where the directory is that you’re trying to go to. In your OP, you said that you can see it under home, then, in another post you say that it is under Templates.

If you go to page 219 in that same Linux commands book, you will see how to use the find command. You can use it to find the absolute path to a directory (and many other uses). If you think the directory you are looking for is under Home somewhere, then I think find would look something like this:

```
find ~ -type d -name veeam
```

If the director you are looking for is behind Home (~ or ~/), then this should return the absolute path to that directory. You can then cd into that directory using that full path.

Do some reading and learn how to navigate using relative path commands because that will greatly speed up your work.

---

### Post by deadflowr on 2024-07-05
I'd use TAB completion to find what the real file name is.
Type the first couple letters then the TAB button which will autofill the rest, if the file exists it will show the actual name.

Also,
> Navigate to the directory where you have saved the veeam-release package and install the package using the command for your Linux distribution.
It's fairly clear you're not suppose the cd into any veeam directory. Unless you somehow had foresight and created a veeam folder before you even downloaded the item at hand.

If the package is for Ubuntu then it's a deb, most likely.
In which case I'd run
```
sudo apt install ./vee+TAB-button
```
As long as the name starts with vee TAB completion should autofill the rest.

---

