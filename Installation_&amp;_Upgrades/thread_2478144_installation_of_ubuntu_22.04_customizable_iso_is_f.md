---
title: "installation of ubuntu 22.04 customizable iso is failing at apt step during install"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by seens on 2022-08-18
We took plain ubuntu 22.04 live server iso, added in-house deb package and bundled as as ISO and at the time of install it is crashing at apt step.

when we manually install the deb package inside system, it is installing with one warning in end, warning: N: **Download is performed unsandboxed as root as file '/root/cobra-bsp_8.0.0.0-47_all.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)**

curtin logs
-----------
Apt Mirror info: {'PRIMARY': 'http://archive.ubuntu.com/ubuntu/', 'SECURITY': 'http://security.ubuntu.com/ubuntu/', 'MIRROR': 'http://archive.ubuntu.com/ubuntu/'}
Applying debconf selections
Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'debconf-set-selections'] with allowed return codes [0] (capture=True)
Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg-query', '--list'] with allowed return codes [0] (capture=True)
finish: cmd-install/stage-curthooks/builtin/cmd-curthooks/writing-apt-config: FAIL: configuring apt configuring apt
finish: cmd-install/stage-curthooks/builtin/cmd-curthooks: FAIL: curtin command curthooks
Traceback (most recent call last):
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/main.py", line 202, in main
    ret = args.func(args)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 1886, in curthooks
    builtin_curthooks(cfg, target, state)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 1692, in builtin_curthooks
    do_apt_config(cfg, target)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 97, in do_apt_config
    apt_config.handle_apt(apt_cfg, target)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/apt_config.py", line 73, in handle_apt
    apply_debconf_selections(cfg, target)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/apt_config.py", line 162, in apply_debconf_selections
    pkgs_installed = distro.get_installed_packages(target)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/distro.py", line 453, in get_installed_packages
    (out, _) = subp(['dpkg-query', '--list'], target=target, capture=True)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/util.py", line 275, in subp
    return _subp(*args, **kwargs)
  File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/util.py", line 139, in _subp
    raise ProcessExecutionError(stdout=out, stderr=err,
curtin.util.ProcessExecutionError: Unexpected error while running command.
Command: ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg-query', '--list']
Exit code: 2
Reason: -
Stdout: ''
Stderr: dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 1913 package 'file':
         multiple non-coinstallable package instances present; most probably due to an upgrade from an unofficial dpkg


Unexpected error while running command.
Command: ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg-query', '--list']
Exit code: 2
Reason: -
Stdout: ''
Stderr: dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 1913 package 'file':
         multiple non-coinstallable package instances present; most probably due to an upgrade from an unofficial dpkg


curtin: Installation failed with exception: Unexpected error while running command.
Command: ['curtin', 'curthooks']
Exit code: 3
Reason: -
Stdout: start: cmd-install/stage-curthooks/builtin/cmd-curthooks: curtin command curthooks
        Running curtin builtin curthooks
        Configuring target system for distro: ubuntu osfamily: debian
        start: cmd-install/stage-curthooks/builtin/cmd-curthooks/writing-apt-config: configuring apt configuring apt
        Transferred {'subiquity': ''} into new format: {'debconf_selections': {'subiquity': ''}}
        curthooks handling apt to target /target with config {'debconf_selections': {'subiquity': ''}}
        Running command ['unshare', '--help'] with allowed return codes [0] (capture=True)
        Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'lsb_release', '--all'] with allowed return codes [0] (capture=True)
        Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg', '--print-architecture'] with allowed return codes [0] (capture=True)
        got primary mirror: None
        got security mirror: None
        Apt Mirror info: {'PRIMARY': 'http://archive.ubuntu.com/ubuntu/', 'SECURITY': 'http://security.ubuntu.com/ubuntu/', 'MIRROR': 'http://archive.ubuntu.com/ubuntu/'}
        Applying debconf selections
        Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'debconf-set-selections'] with allowed return codes [0] (capture=True)
        Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg-query', '--list'] with allowed return codes [0] (capture=True)
        finish: cmd-install/stage-curthooks/builtin/cmd-curthooks/writing-apt-config: FAIL: configuring apt configuring apt
        finish: cmd-install/stage-curthooks/builtin/cmd-curthooks: FAIL: curtin command curthooks
        Traceback (most recent call last):
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/main.py", line 202, in main
            ret = args.func(args)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 1886, in curthooks
            builtin_curthooks(cfg, target, state)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 1692, in builtin_curthooks
            do_apt_config(cfg, target)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 97, in do_apt_config
            apt_config.handle_apt(apt_cfg, target)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/apt_config.py", line 73, in handle_apt
            apply_debconf_selections(cfg, target)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/commands/apt_config.py", line 162, in apply_debconf_selections
            pkgs_installed = distro.get_installed_packages(target)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/distro.py", line 453, in get_installed_packages
            (out, _) = subp(['dpkg-query', '--list'], target=target, capture=True)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/util.py", line 275, in subp
            return _subp(*args, **kwargs)
          File "/snap/subiquity/3359/lib/python3.8/site-packages/curtin/util.py", line 139, in _subp
            raise ProcessExecutionError(stdout=out, stderr=err,
        curtin.util.ProcessExecutionError: Unexpected error while running command.
        Command: ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg-query', '--list']
        Exit code: 2
        Reason: -
        Stdout: ''
        Stderr: dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 1913 package 'file':
                 multiple non-coinstallable package instances present; most probably due to an upgrade from an unofficial dpkg


        Unexpected error while running command.
        Command: ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg-query', '--list']
        Exit code: 2
        Reason: -
        Stdout: ''
        Stderr: dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 1913 package 'file':
                 multiple non-coinstallable package instances present; most probably due to an upgrade from an unofficial dpkg




Stderr: ''

---

### Post by damasker on 2022-09-14
Hi! 
You found solution?

---

### Post by seens on 2022-11-08
Nope, not working and need help.[ATTACH]291230[/ATTACH]

attached the curtain error log files.

---

