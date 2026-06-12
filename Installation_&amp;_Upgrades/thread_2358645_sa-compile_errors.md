---
title: "sa-compile errors"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-04-15
I upgraded a system from 214.04 to 16.04 and as usual had a few issues. 

One I am stuck on is sa-compile errors.

```
Can't exec "rm": No such file or directory at /usr/bin/sa-compile line 374, <$fh> line 1.
```

Obviously rm is on the machine but sa-compile won't complete. Googling that error I found some references but no solution.

---

### Post by rsteinmetz70112 on 2017-04-19
I've investigated as-compile, it is a perls scrip and the errors are at least partly the result of  perl not being able to find certain system commands specifically rm, stty and chmod. 

All are in place and works from the login shell adn form any interactive shell, but don't work from a perl script unless the full path is specified. I have confirmed that by editing the perl script and including the full path for rm, unfortunately the other commands seem to be call from other scripts either called from sa-compile or its successors.

It seems apparent there is an error in my configuration but I can't find it. dpkg --configure -a runs with only and error for sa-compile.

I have found references to an @INC path for perl, but it's unclear whether it applies only to perl scripts of if it the equivalent of $PATH for a shell.

It;s also unclear why it's not set correctly.

---

### Post by rsteinmetz70112 on 2017-04-21
With the help of some people on the Spamassassin list I have found the problem.

Spam assassin checks the permission of the directories in the search path and if any are are readable buy any user except the owner and group then the equivalent of $PATH is not set inside perl. If you see this error check the ownership and permissions of every directory in $PATH they generally should be root root and 775.

Here's how it was explained to me:

> The sa-compile script DOES use a SA utility function to untaint the whole %ENV hash, but there's a special catch for $ENV{'PATH'}: if any directories included are not absolute (e.g. commonly '.' and '~/bin') OR are writable by more than their owning user & group, $ENV{'PATH'} remains tainted and won't be used or passed to child processes.

---

