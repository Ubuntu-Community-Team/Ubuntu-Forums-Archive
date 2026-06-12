---
title: "rsync fails after upgrade to 14.04"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by jack_glendening on 2014-05-29
After upgrading from 13.10 to 14.04 my rsync to a remote server is now
failing with message

  [I]protocol version mismatch - is your shell clean?
  (see the rsync man page for an explanation)
  rsync error: protocol incompatibility (code 2) at compat.c(62)
  rsync: connection unexpectedly closed (0 bytes received so far) [sender]
  rsync error: error in rsync protocol data stream (code 12) at io.c(226) [sender=3.1.0][/I]

This was coming from a cron job run daily on my local machine - it
worked successfully until the day after the upgrade.  I also get the
same error when running a command-line rsync ala
  *rsync /home/user/DIR user@remotehost/DIR*

Nothing on the remote machine's rsync or ssh has been changed (nor has
anything else of any significance)

An on-line search says this is normally due to startup scripts or
remote shell facility producing unwanted garbage.  But testing for
such by running
  *rsh user@remotehost /bin/true*
produces a zero-length file, as it should, to indicate there is no "unwanted garbage" in my 
startup scripts (and that command does not give
any error meesage, successfully logging into the remote host).
Just to make sure, I ran the startup scripts (.bashrc, etc) on the remote machine
via the command-line (after remotely logging on) and no output was observed.

Another thing suggested was to check whether rsync is installed and locatable by ssh.
So I ran
  *ssh user@remotehost "rsync --version"*
and got a successful result, with no error messages:
  [I]rsync  version 2.5.7  protocol version 26
  Copyright (C) 1996-2002 by Andrew Tridgell and others
  <http://rsync.samba.org/>
  Capabilities: 64-bit files, socketpairs, hard links, symlinks, batchfiles,
                IPv6, 64-bit system inums, 64-bit internal inums
  rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
  are welcome to redistribute it under certain conditions.  See the GNU
  General Public Licence for details.
[/I]
Running "rsync --version" on my local machine gives
  [I]rsync  version 3.1.0  protocol version 31
  Copyright (C) 1996-2013 by Andrew Tridgell, Wayne Davison, and others.
  Web site: [http://rsync.samba.org/](http://rsync.samba.org/)
  Capabilities:
      64-bit files, 64-bit inums, 32-bit timestamps, 64-bit long ints,
      socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
      append, ACLs, xattrs, iconv, symtimes, prealloc
  rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
  are welcome to redistribute it under certain conditions.  See the GNU
  General Public Licence for details.[/I]


As I say, nothing on the remote machine has changed so the error must
be resulting from some change on my local machine produced by the
ubuntu upgrade. I've run out of things to try that I could find on-line,
so hoping to find someone here who can see why the ubuntu upgrade might
have caused this problem.

SOLVED
In case this helps others, solution appears to be that the rsync used by 14.04
 uses a different protocol than 13.10  so I must add  --protocol=26 to my rsync call.

---

### Post by papibe on 2014-06-02
Hi jack_glendening. Welcome to the forum ):P

I'm glad you solved your problem.

I just wanted to point out a possible security issue. The rsync version you are running (2.5.7) is from 2003. This makes me think that your OS is  around that time, or possible even older.

If this server is available to the Internet, I would be concern if it still receives security updates.

Just a thought.

Come here often and have fun.
Regards.

---

### Post by simplr on 2015-04-18
> **jack_glendening said:**
> After upgrading from 13.10 to 14.04 my rsync to a remote server is now
failing with message

  [I]protocol version mismatch - is your shell clean?
  (see the rsync man page for an explanation)
  rsync error: protocol incompatibility (code 2) at compat.c(62)
  rsync: connection unexpectedly closed (0 bytes received so far) [sender]
  rsync error: error in rsync protocol data stream (code 12) at io.c(226) [sender=3.1.0][/I]

...

SOLVED
In case this helps others, solution appears to be that the rsync used by 14.04
 uses a different protocol than 13.10  so I must add  --protocol=26 to my rsync call.

Thanks very much for posting this solution. It worked for me and probably saved me a lot of time. FYI the remote server with the problem is still running Fedora Core 1, installed in 2005.
Regards
Norman

---

