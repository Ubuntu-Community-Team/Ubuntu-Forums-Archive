---
title: "Fix Computer-janitor or remove it"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-02-25
I think a lot of you have noticed that when running Computer-janitor it wants to clean away all the packages that are not from the repositories. If I for example download a package from getdeb and installs, it is going to be removed by Computer-janitor.

Does anyone know if there is a bugreport on this or should I file one?

---

### Post by taavikko on 2009-02-25
[https://bugs.launchpad.net/ubuntu/+source/computer-janitor](https://bugs.launchpad.net/ubuntu/+source/computer-janitor)

GUI isn't installed by default, so no harm there...
CLI is meant for little more experienced users and as always there's a manual for it.

Isn't there a tickbox to check if you don't want something to be removed?

---

### Post by Nullack on 2009-02-25
It was poorly tested and as a result lacks robustness.

---

### Post by olskar on 2009-02-25
> **taavikko said:**
> [https://bugs.launchpad.net/ubuntu/+source/computer-janitor](https://bugs.launchpad.net/ubuntu/+source/computer-janitor)

GUI isn't installed by default, so no harm there...
CLI is meant for little more experienced users and as always there's a manual for it.

Isn't there a tickbox to check if you don't want something to be removed?

Ah, I see :) Then it's not a very big problem.

---

### Post by taavikko on 2009-02-25
> **taavikko]GUI isn't installed by default, so no harm there...
[QUOTE=olskar said:**
> Ah, I see :) Then it's not a very big problem.
[/quote]

So, seems I spoke little too hasty, just got pulled by an update to ubuntu-desktop (computer-janitor-gtk)

But it still has checkbox to tick if something doesn't want to be removed...

---

### Post by Nullack on 2009-02-25
We all should try to test this out some more before it hits beta. Im going to give it some functional tests.

---

### Post by olskar on 2009-02-25
> **taavikko said:**
> So, seems I spoke little too hasty, just got pulled by an update to ubuntu-desktop (computer-janitor-gtk)

But it still has checkbox to tick if something doesn't want to be removed...

Yes, but I still think it's a bug. Manually installed packages is not 'cruft'

---

### Post by obscur156 on 2009-02-25
I have to agree olskar,Manually installed packages is not 'cruft'.

If you really need something to clean your Pc you can try [COLOR="Blue"]Bleachbit[/COLOR] ,its in the repos or you can have a look  here:
 [COLOR="RoyalBlue"][http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")[/COLOR]

I really like that one.
Regards,have a nice day.

---

### Post by olskar on 2009-02-25
> **obscur156 said:**
> I have to agree olskar,Manually installed packages is not 'cruft'.

If you really need something to clean your Pc you can try [COLOR="Blue"]Bleachbit[/COLOR] ,its in the repos or you can have a look  here:
 [COLOR="RoyalBlue"][http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")[/COLOR]

I really like that one.
Regards,have a nice day.

:o

Seriosly! Why isn't that included instead of Computer-Jantitor?

---

### Post by Mr. Picklesworth on 2009-02-25
> **Nullack said:**
> It was poorly tested and as a result lacks robustness.

That's why you're [here]("http://ubuntuforums.org/forumdisplay.php?f=352").

---

### Post by obscur156 on 2009-02-25
> Seriosly! Why isn't that included instead of Computer-Jantitor?
I dont know olskar,you should ask the developer!

---

### Post by | MM | on 2009-02-25
> **obscur156 said:**
> 
 [COLOR="RoyalBlue"][http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")[/COLOR]


Wow thats great i just cleaned up 560 MB of 'cruft' -- hope things keep working.  But BleachBits can't do much in the way of removing old  or unnecessary packages... it just removes cache's and other files of installed apps.  Bleachbits functionality should be incorporated into the janitor, though.

---

### Post by Jimbob0i0 on 2009-02-26
> **Mr. Picklesworth said:**
> That's why you're [here]("http://ubuntuforums.org/forumdisplay.php?f=352").

Yup - which is why I just filed a bug in launchpad outlining why this is a problem :)

[https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/334790](https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/334790)

And I agree beachbit should be incorporated... but I guess that's too late for jaunty now given that we are past featurefreeze... a blueprint should be created for koala though.

---

### Post by kurros on 2009-02-26
The primary use of this is to remove obsolete packages, unsupported 3rd party packages, old kernels and setup other things (relatime, etc) in a distribution upgrade.

See the computer-janitor man page for information about creating a whitelist in /etc/computer-janitor.d of packages to ignore. Or just add it using the computer-janitor ignore command. The computer-janitor ignore/unignore commands are not properly exposed in the GTK+ interface yet, and GUI documentation is coming.

This came up in its development (see [bug 285746]("https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746") for example) but the crux is that there is no way to tell the difference between a really obsolete package and one installed with dpkg --install. There are several different warnings when you attempt to remove one of these packages. If you are not getting these warnings for local packages then that would be a bug.


Guys this is under System->Administration not Applications->Accessories. Your grandma isn't going to accidentally remove anything using this tool between that and the "This may break your system" warning.

---

### Post by olskar on 2009-02-26
> **kurros said:**
> The primary use of this is to remove obsolete packages, unsupported 3rd party packages, old kernels and setup other things (relatime, etc) in a distribution upgrade.

See the computer-janitor man page for information about creating a whitelist in /etc/computer-janitor.d of packages to ignore. Or just add it using the computer-janitor ignore command. The computer-janitor ignore/unignore commands are not properly exposed in the GTK+ interface yet, and GUI documentation is coming.

This came up in its development (see [bug 285746]("https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746") for example) but the crux is that there is no way to tell the difference between a really obsolete package and one installed with dpkg --install. There are several different warnings when you attempt to remove one of these packages. If you are not getting these warnings for local packages then that would be a bug.


Guys this is under System->Administration not Applications->Accessories. Your grandma isn't going to accidentally remove anything using this tool between that and the "This may break your system" warning.

My grandma propably thinks Computer-janitor sounds cozy and homishly :)

But I get your point

---

### Post by Mr. Picklesworth on 2009-02-26
Don't these both do fairly different tasks, though? Bleachbit deals with things like cache for the sole purpose of freeing (a great deal of) disk space and a bit of memory, whereas system-cleaner / cruft-remover / computer-janitor removes... cruft left over from upgrades (like unused configuration files, unused packages that apt-get autoremove won't notice).

---

### Post by Jimbob0i0 on 2009-02-26
> **kurros said:**
> The primary use of this is to remove obsolete packages, unsupported 3rd party packages, old kernels and setup other things (relatime, etc) in a distribution upgrade.

See the computer-janitor man page for information about creating a whitelist in /etc/computer-janitor.d of packages to ignore. Or just add it using the computer-janitor ignore command. The computer-janitor ignore/unignore commands are not properly exposed in the GTK+ interface yet, and GUI documentation is coming.

This came up in its development (see [bug 285746]("https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746") for example) but the crux is that there is no way to tell the difference between a really obsolete package and one installed with dpkg --install. There are several different warnings when you attempt to remove one of these packages. If you are not getting these warnings for local packages then that would be a bug.


Guys this is under System->Administration not Applications->Accessories. Your grandma isn't going to accidentally remove anything using this tool between that and the "This may break your system" warning.

Just read your link - shame there wasn't a link back to the original package from computer-janitor to system-cleaner back when intrepid was being developed. 

Looking through the old big notes the same problem was highlighted then with the consequence of it being removed from the ubuntu-desktop metapackage and that work to identify manually installed packages somehow would be done for jaunty.....

I fail to see in what way it has progressed from system-cleaner back then and as such why it should be a default package via ubuntu-desktop.....

It may be in System Administration - but then so is update manager, date and time and printer administration....

If it is at the point where 'this may break your system are you sure?' is required then it really is pointed towards more advanced users who know what the packages are for... who could make use of synaptic instead for the same purpose.

If there is a genuine reason why it has progressed to the point it is a useful enough utility to be installed by default note it on my bug report why - or at least make a comment yourself pointing to the old system-cleaner package - I would be interested to hear your reasoning.

---

