---
title: "installing a program (Guassian 16)"
date: 2017-05-01
forum: Installation &amp; Upgrades
---

### Post by eelie on 2017-05-01
Hello,

im trying to install a program called Gaussian 16 to U17.04. it has these instructions which I don't really understand but is from what I know, makes the install straightforward.

questions:
1. Skipping to step 3, I have it on a USB, how do I mount a USB? what does this even mean?

2. I installed csh (via sudo apt-get install csh) when I try to do step 4, and type the % lines, what next?

----------------------------------------------
     UNIX Binary Gaussian 16 Revision A.03 Installation instructions

1.  Check that you have the correct versions of the OS, and libraries for
    your machine, as listed in the file platform_a03.pdf file on G16 DVD.
    Release notes can be found in release_a03.txt.

2.  Select a group which will own the Gaussian files. Users who will
    run Gaussian should either already be in this group, or should
    have this added to their list of groups. Consult your system
    administrator if you need help with this process.

3.  Mount the DVD, or determine where the system has mounted it
    automatically.

4.  Change to the C shell, and set the g16root and mntpnt environment 
    variables:

    $ /bin/csh
    % setenv mntpnt "/mnt/dvd"         # Set to wherever dvd is mounted.
    % setenv g16root "<dir>"           # Set to install location for G16.
    % cd $g16root

5.  Read the DVD and run the script which sets group ownership:

    % bzip2 -d -c $mntpnt/tar/*.tbz | tar xvf -
    % chgrp -R <grp> g16               # <grp> is the group from step 1.
    % cd g16
    % bsd/install

6.  You are now ready to run.  Users will want to add the following to
    their .login file if they are using the tcsh:

    setenv g16root "<dir>"              
    setenv GAUSS_SCRDIR "<scr-dir>"
    source $g16root/g16/bsd/g16.login     # sets up G16 run environment.

    Bash users should include the following in their .bash_profile

    g16root="<dir>"
    GAUSS_SCRDIR="<scr-dir>"
    export g16root GAUSS_SCRDIR
    . $g16root/g16/bsd/g16.profile

    The <dir> in the first command is the location of the g16 directory.
    For example, if the path to this directory is /usr/local/g16, then
    set g16root to /usr/local. The <scr-dir> in the second command is
    a directory to be used by default for Gaussian 16 scratch files.
    There should be plenty of disk space available at this location.
    Note that the angle brackets are NOT included.

---

### Post by Impavidus on 2017-05-02
1: Unless you modified your system to do otherwise, the usb should be mounted automatically at /media/yourusername/somelabel/. Else you have to use the mount command. Mounting is the action of attaching the file system on the usb to the root file system of your Ubuntu system.

2: Just type the commands. The % sign indicates you should have a csh prompt there. So don't type the % signs.

---

