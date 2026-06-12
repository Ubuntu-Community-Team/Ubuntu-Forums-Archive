---
title: "Is it possible to use umake to install outside of the /home/ dirtree?"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by clunk2 on 2016-12-07
0         down vote          [favorite]("http://askubuntu.com/questions/857891/umake-permission-denied-when-installing-outside-home-directory-even-as-root?noredirect=1#")                                        [TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]        I'm trying to install firefox-dev using umake. By default the umake install path is `~/.local/share/`; I'd rather it was in `/usr/local/` or `/opt/`.
  The problem appears to be umake (or, rather, the `os.py` script it  runs) not having permission to create files/directories - this happens  even when I'm running as an admin user elevated using `sudo`, or I've switched to the root user using `sudo -i`.

  Here's an example of the relevant error:

      [HTML]os.makedirs(self.install_path, exist_ok=True)
  File "/usr/lib/python3.5/os.py", line 231, in makedirs
    makedirs(head, mode, exist_ok)
  File "/usr/lib/python3.5/os.py", line 241, in makedirs
    mkdir(name, mode)
PermissionError: [Errno 13] Permission denied: '/opt/umake' 
[/HTML]

Command run is `sudo umake web firefox-dev`. Does not matter where I run it. 
  As for install paths (entered into the prompt during install  attempts), I've tried all options from explicitly declared  absolute paths (including creating the dirtree myself, which ultimately  and unsurprisingly just pushes the error messages back to file creation)  to being in the target dir and using './'.

  I have no problems doing anything as root myself, but  those permissions don't seem to be being inherited by the python install  script(s).

Is there any way I can get umake to let me install items where I want it to?
[/TD]
[/TR]
[/TABLE]

---

