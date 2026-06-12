---
title: "HOWTO APT-BUILD in webmin software module"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by alecuba16 on 2011-05-31
Hello i modified my webmin software packages module to do apt-build instead apt-get 

You have to change 4 lines: 

in   /usr/share/webmin/software/apt-lib.pl
from
```
$apt_get_command = $config{'apt_mode'} ? "aptitude" :"apt-get";
```
to
```
$apt_get_command = $config{'apt_mode'} ? "aptitude" :"apt-build";
```

in /usr/share/webmin/software/apt-lib.pl
from
```
local $cmd = $apt_get_command eq "apt-get" ?
```
to
```
local $cmd = $apt_get_command eq "apt-build" ?
```

in /usr/share/webmin/software/apt-lib.pl
from
```
my $cmd = "apt-get -s install ". 
```

to
```
my $cmd = "apt-build -s install ".
```

in /usr/share/webmin/software/software-lib.pl
from
```
if (&has_command($config{'apt_mode'} ? "aptitude" : "apt-get")) {
```

to
```
if (&has_command($config{'apt_mode'} ? "aptitude" : "apt-build")) {
```


in /usr/share/webmin/software/apt_upgrade.cgi
from
```

if ($in{'mode'}) {
        $opts = $in{'sim'} ? "-s -y -f" : "-y -f";
        $cmd = $in{'mode'} == 2 ? "dist-upgrade" :
               $apt_get_command =~ /aptitude/ ? "safe-upgrade" : "upgrade";
        print "<b>",&text($in{'sim'} ? 'apt_upgradedescsim' : 'apt_upgradedesc', "<tt>$apt$
        print "<pre>";
        &additional_log("exec", undef, "$apt_get_command $opts $cmd");
        &clean_environment();
        open(CMD, "$apt_get_command $opts $cmd 2>&1 </dev/null |");

```

to

```

if ($in{'mode'}) {
        $opts = $in{'sim'} ? "-s -y -f" : "-y -f";
        $cmd = $in{'mode'} == 2 ? "dist-upgrade" :
               $apt_get_command =~ /aptitude/ ? "safe-upgrade" : "upgrade";
        print "<b>",&text($in{'sim'} ? 'apt_upgradedescsim' : 'apt_upgradedesc', "<tt>$apt$
        print "<pre>";
        if($cmd == "dist-upgrade")
          {
           &additional_log("exec", undef, "apt-get $opts $cmd");
           &clean_environment();
           open(CMD, "apt-get $opts $cmd 2>&1 </dev/null |");
          }
          else{
           &additional_log("exec", undef, "$apt_get_command $opts $cmd");
           &clean_environment();
        open(CMD, "$apt_get_command $opts $cmd 2>&1 </dev/null |");
        }

```

This last modification is for do dist-upgrade with apt-get because apt-build don't have this option.

Now you have support to compile (build) packages from webmin and not to break or reemplace with apt-get.

---

