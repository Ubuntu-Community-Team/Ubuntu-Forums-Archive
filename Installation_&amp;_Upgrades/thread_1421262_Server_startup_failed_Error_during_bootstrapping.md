---
title: "Server startup failed: Error during bootstrapping"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by bluecure on 2010-03-04
Hi, I realize this probably isn't the best place to be posting this as it relates to project open, but they don't have a forum.

We recently upgraded our Ubuntu server and now when trying to use project open we get the follow error message, does anyone know why this may be, or have any guesses as to why this may be. 

Server startup failed: Error during bootstrapping 
No fullquery for dbqd.acs-tcl.tcl.apm-procs.apm_package_installed_p_not_cached.apm_package_installed_p and default SQL empty - query for statement missing
    while executing
"error "No fullquery for $statement_name and default SQL empty - query for statement missing""
    (procedure "db_qd_replace_sql" line 10)
    invoked from within
"db_qd_replace_sql $statement_name $pre_sql"
    (procedure "db_exec" line 12)
    invoked from within
"db_exec 0or1row $db $full_name $sql"
    invoked from within
"set selection [db_exec 0or1row $db $full_name $sql]"
    ("uplevel" body line 2)
    invoked from within
"uplevel 1 $code_block "
    invoked from within
"db_with_handle -dbn $dbn db {
        set selection [db_exec 0or1row $db $full_name $sql]
    }"
    (procedure "db_string" line 8)
    invoked from within
"db_string apm_package_installed_p {} -default 0"
    (procedure "apm_package_installed_p_not_cached" line 2)
    invoked from within
"apm_package_installed_p_not_cached $package_key"
    (procedure "apm_package_installed_p" line 5)
    invoked from within
"apm_package_installed_p acs-kernel"
    (procedure "ad_verify_install" line 6)
    invoked from within
"ad_verify_install"  

Thanks

---

### Post by robertkip on 2010-04-16
i tried installing it also, and got exactly the same output. I am curious to know what the solution is. thanks

---

### Post by rogerolivet on 2010-05-05
I  have the same problem using ubuntu 10.04. (just used the instalation script from [http://www.project-open.org/documentation/install_ubuntu](http://www.project-open.org/documentation/install_ubuntu) )

thanks!

---

### Post by Cryophallion on 2010-05-06
I had the same issue. I'm going to try it with 8.04 and see if it works any better.

---

### Post by Cryophallion on 2010-05-07
8.04.4 appears to have failed as well.

---

### Post by dino99 on 2010-05-07
need to file a bug report

---

### Post by Cryophallion on 2010-05-07
I couldn't find a bug reporting section on the website. Did finally find the sourceforge forum, and it has been posted:

[http://sourceforge.net/projects/project-open/forums/forum/295937/topic/3700783](http://sourceforge.net/projects/project-open/forums/forum/295937/topic/3700783)

---

### Post by TangLung on 2010-07-11
> **Cryophallion said:**
> I couldn't find a bug reporting section on the website. Did finally find the sourceforge forum, and it has been posted:

[http://sourceforge.net/projects/project-open/forums/forum/295937/topic/3700783](http://sourceforge.net/projects/project-open/forums/forum/295937/topic/3700783)

Hi all,

just to let you know we finally have a fix for this.

Venkat Mangudi, Projop Ubuntu installer's mantainer, just post a few lines on sourceforge forum on the topic above (in the installer script there was a broken version of tdom that doesn't compile correctly so now you can download the fixed version at the same address -> wget [http://www.venkatmangudi.com/project-open-34/po-install-script-64bit.sh](http://www.venkatmangudi.com/project-open-34/po-install-script-64bit.sh)  for the 64bit version) and below you can find my answer there, that I'm reporting here too for your convenience, hoping it can help whoever got this problem.

> 
Hi Venkat,

First of all, thank you for the solution.

I had this same install problem and I almost managed to fix it installing tdom from repositories (on a karmic 64bit server): 

Projop | OpenACS then started but with auth problems ( wrong # args: should be "AcsSc.auth_authentication.authenticate.local username ) as a response every time I tried to log in using any of the demo server accounts.

So I tried recompiling nspostgres to get a new nspostgres.so db module  - then adding nsxml - and even messing with the config.tcl file modifying settings for db polls - but without any luck.

Now, getting tdom with git clone and compiling it everything works fine, and the server finally is up.

For those that already installed ]po[ 3.4 on ubuntu, just like me: you've not to run the whole script again.

Just type:

```

sudo apt-get install git-core
cd /usr/local/src/aolserver-4.5.1
git clone http://github.com/makr/tdom.git
cd tdom/unix
../configure --enable-threads --disable-tdomalloc --prefix=/usr/lib/aolserver4 --exec-prefix=/usr/lib/aolserver4 --with-aolserver=/usr/lib/aolserver4 --with-tcl=/usr/local/src/tcl8.5.6/unix
make install

```At the end of the process just stop and restart the server and everything will work like a charm.

Thank you again and a nice new week to everyone :o)

Fabrizio
That's all. folks! :D

---

