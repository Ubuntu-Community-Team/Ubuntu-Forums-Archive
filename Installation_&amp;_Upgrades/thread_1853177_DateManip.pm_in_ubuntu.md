---
title: "Date/Manip.pm in ubuntu"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by itba on 2011-10-01
hi, I had Date::Manip running but I was trying to call a perl program from C++ and it seemed like I needed ExtUtils. so  I ran 
```
force install ExtUtils::Embed
```it did it's thing but now I get the following error
```
Can't locate Date/Manip.pm in @INC (@INC contains: /usr/local/lib/perl5/site_perl/5.15.2/i686-linux /usr/local/lib/perl5/site_perl/5.15.2 /usr/local/lib/perl5/5.15.2/i686-linux /usr/local/lib/perl5/5.15.2 .) 
```I went into CPAN and ran ```
force install Date::Manip
```, but it doesn't seem to work...I get the following error
```

Building Date-Manip
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/local/lib/perl5/site_perl/5.15.2/Date'
Do not have write permissions on '/usr/local/lib/perl5/site_perl/5.15.2/Date'
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at /usr/local/lib/perl5/5.15.2/Module/Build/Base.pm line 3574
  SBECK/Date-Manip-6.25.tar.gz
  ./Build install  -- NOT OK
Failed during this command:
 SBECK/Date-Manip-6.25.tar.gz                 : install NO

```
how do I give myself write permissions to that directory....

---

