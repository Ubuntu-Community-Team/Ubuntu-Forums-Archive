---
title: "Problem upgrading metasploit framework 3.3"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by athevil on 2010-01-18
Hi all,

Getting error while updating metasploit usind 'mafupdate'

the error:> Updating Metasploit from [https://www.metasploit.com/svn/framework3/trunk](https://www.metasploit.com/svn/framework3/trunk)...
svn: Working copy '.' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
 
Error: cleaning up the SVN directory and retrying...
svn: In directory 'modules/auxiliary/scanner/mysql'
svn: Error processing command 'modify-wcprop' in 'modules/auxiliary/scanner/mysql'
svn: 'modules/auxiliary/scanner/mysql/mysql_login.rb' is not under version control
svn: Working copy '.' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
 
Error: please check connectivity to the following URL:
    [https://www.metasploit.com/svn/framework3/trunk](https://www.metasploit.com/svn/framework3/trunk)


tried to run 'svn cleanup' (without even knowing what actually it does :P)

gave me 
> svn: '.' is not a working copy directoryhelp!:(

---

### Post by hdmoore on 2010-01-18
It looks like the SVN repository was corrupted, somehow. Try this: 

$ sudo rm -rf  /opt/metasploit3/msf3/modules/auxiliary/scanner/mysql/
$ sudo msfupdate

---

### Post by athevil on 2010-01-18
hey that solved it man

many thanks
was wandering all over the world, b4 posting it...thanks again

---

### Post by mohammad6006 on 2010-12-06
> **hdmoore said:**
> It looks like the SVN repository was corrupted, somehow. Try this: 

$ sudo rm -rf  /opt/metasploit3/msf3/modules/auxiliary/scanner/mysql/
$ sudo msfupdate

i run $ sudo rm -rf  /opt/metasploit3/msf3/

and now when i run update show : Skipped '/opt/metasploit3/msf3'

what can i do?

help me :(

---

