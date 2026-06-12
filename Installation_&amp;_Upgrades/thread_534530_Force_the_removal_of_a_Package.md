---
title: "Force the removal of a Package?"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by gxwilson on 2007-08-25
Newbie question but here goes.

I've screwed up my install of MySql 5.0 and I'm trying to just start it over. I've used apt to remove but it always seemed to leave many of the directories in place along with the etc/mysql dir which seems to have screwed me up. 

Now can't install the mysql-server-5.0 package. Nothing gets created but apt-get install says everything is good?!?

The install error now is:" invoke-rc.d: unknown initscript, /etc/init.d/mysql not found."

How do I get apt in synch with my box's real state?

Thanks

---

### Post by Pumalite on 2007-08-25
Try: sudo dpkg --remove --force-remove-<packagename>
Then try again.

Another thing to do first maybe: sudo dpkg --configure -a

---

### Post by gxwilson on 2007-08-25
dpkg didn't like "sudo dpkg --remove --force-remove-<packagename>" but "sudo dpkg --remove <packagename>" works and 'sudo dpkg --purge <packagename>" moved things a step closer. 

Problem now seems that "sudo apt-get install mysql-server-5.0" fails with the following error:
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory

---

### Post by Pumalite on 2007-08-25
That's what 'force-remove' is for: to remove all vestiges of a program. What do you mean: 'dpkg didn't like it'?

---

### Post by gxwilson on 2007-08-25
If I do:
[HTML]sudo dpkg --remove --force-remove mysql-server-5.0[/HTML]

then I get:
[HTML]dpkg: unknown force/refuse option `remove'[/HTML]

if I type:
[HTML]dpkg --force-help
dpkg forcing options - control behaviour when problems found:
  warn but continue:  --force-<thing>,<thing>,...
  stop with error:    --refuse-<thing>,<thing>,... | --no-force-<thing>,...
 Forcing things:
  all [!]                Set all force options
  downgrade [*]          Replace a package with a lower version
  configure-any          Configure any package which may help this one
  hold                   Process incidental packages even when on hold
  bad-path               PATH is missing important programs, problems likely
  not-root               Try to (de)install things even when not root
  overwrite              Overwrite a file from one package with another
  overwrite-diverted     Overwrite a diverted file with an undiverted version
  bad-verify             Install a package even if it fails authenticity check
  depends-version [!]    Turn dependency version problems into warnings
  depends [!]            Turn all dependency problems into warnings
  confnew [!]            Always use the new config files, don't prompt
  confold [!]            Always use the old config files, don't prompt
  confdef [!]            Use the default option for new config files if one
                         is available, don't prompt. If no default can be found,
                         you will be prompted unless one of the confold or
                         confnew options is also given
  confmiss [!]           Always install missing config files
  conflicts [!]          Allow installation of conflicting packages
  architecture [!]       Process even packages with wrong architecture
  overwrite-dir [!]      Overwrite one package's directory with another's file
  remove-reinstreq [!]   Remove packages which require installation
  remove-essential [!]   Remove an essential package

WARNING - use of options marked [!] can seriously damage your installation.
Forcing options marked [*] are enabled by default.
[/HTML]

---

### Post by Pumalite on 2007-08-25
Somebody that knows about this particular package will have to chime in. Good luck.

---

### Post by gxwilson on 2007-08-25
Actually, after playing with this for a bit I got MySQL reinstalled and I'm all set.

Thanks for the help Pumalite, I think it did get me moving along!!

---

### Post by Pumalite on 2007-08-25
You are welcome. Glad it worked for you.

---

