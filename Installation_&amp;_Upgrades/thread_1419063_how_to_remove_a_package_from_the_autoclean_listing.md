---
title: "how to remove a package from the autoclean listing"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2010-03-01
so if I run `sudo apt-get autoremove`, it gives
me a list of packages that it thinks are no longer needed.
That's fine.

But I would like to tell apt, "hey, take packageA out of that list, cause I really need it, and I do not want to reinstall it out of fear it may mess up the configuration of that very same package".

Anyone know what program and option I would use to accomplish
such a task?

(couldn't find anything interesting under the `apt-get` command.)

---

### Post by ratcheer on 2010-03-01
aptitude has a "keep-all" command. Apt-get probably has it, too.

Tim

---

### Post by gmoore777 on 2010-03-01
thank you for that pointer.

`sudo aptitude unmarkauto <package>`

seems like it would be the solution but although
it does change this entry (via `aptitude show <package>`)
to NOT automatically installed, it still wants to remove it:

  State: installed; will be removed because nothing depends on it
  Automatically installed: no


so then I did:
`sudo aptitude keep <package>` and that changed it to:

  State: installed
  Automatically installed: yes  

So it's good that it no longer wants to remove it, but
then it flipped it back to Automatically installed.

I also am concerned that `aptitude keep` may keep this package
at the current version level and never be able to be updated, but
I'll worry about that some other point in time.

Thanks, I'm all set for now.

---

### Post by ratcheer on 2010-03-01
Yes, most people know more about this stuff than I, but I'm starting to learn my way around, a little.

Tim

---

