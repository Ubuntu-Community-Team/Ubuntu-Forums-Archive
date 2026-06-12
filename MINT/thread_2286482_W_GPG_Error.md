---
title: "W: GPG Error?"
date: 2015-07-12
forum: MINT
---

### Post by ken0069 on 2015-07-12
Got this error the other day when I ran update in terminal.  Please note that this is Mint 17 w/Mate desktop and I installed the Opera browser manually when I first installed mint 17 because Opera wasn't part of the repositories at the time.  Seems that in the past week the Opera key has gone kaput and I'm getting this error on not only Mint 17, but in Ubuntu 14.04 as well with Opera.  

```
W: GPG error: http://deb.opera.com stable InRelease: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY 517590D9A8492E35 NO_PUBKEY 63F7D4AFF6D61D45
```

I uninstalled Opera via Synaptic then ran update in terminal and still got this error.  

Found out that Opera-Next is available in the repositories now so I installed that via Synaptic and after reboot still have the same error??  

Looked for the authentication keys in software update but there are none there for Opera??

It doesn't seem to be causing any problems other than the error that comes up each time I run update in terminal, but I'd really like to fix it?

Any help

Thanks

---

### Post by Bashing-om on 2015-07-12
ken0069; Hello;

As you now have opera installed from the repository, I would think the PPA source is now at the root of the cause and I would remove that old PPA source .
Check:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

ppa purge ? I would think is in-order here .
[http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed)

And in your favorite text editor remove the opera references.

[INDENT][INDENT]all a part of house keeping
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-07-12
Or, go to 'Software and Updates'> Other Software. Find the PPA that has deb.opera.com stable in it somewhere or mentions opera and disable (untick) or remove it. You will then be asked to update. Do it. Smooth ride?

---

### Post by ken0069 on 2015-07-13
Thanks guys.  I managed to get this fixed (I think).  Kept telling me it couldn't find the PPA?  Maybe I didn't type it in correctly?  Ennywho, I ran the following command to remove it manyally.

```
sudo rm -f /etc/apt/sources.list.d/opera.list
```

With your help I was able to "find" the file that needed to be deleted.  Just hope nothing else got broken in the process.  I guess the next day or so will tell that tale.

@ Bucky Ball,  That PPA was not listed in the normal place you would find it in Software Sources?  Dunno why but it wasn't there?  Maybe Mint does something a little different from regular Ubuntu on this type stuff?

---

### Post by Bucky Ball on 2015-07-13
Ok. Missed that bit. In that case, for clarity:

*Thread moved to **MINT**.*

Please post in this forum section for any Mint issues. Your chances may be better on the active Mint forums. Good luck.

---

