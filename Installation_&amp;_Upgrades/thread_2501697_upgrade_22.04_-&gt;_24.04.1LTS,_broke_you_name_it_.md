---
title: "upgrade 22.04 -&gt; 24.04.1LTS, broke you name it  (python please help)"
date: 2024-10-17
forum: Installation &amp; Upgrades
---

### Post by daklein on 2024-10-17
Boy I'm kicking myself, at least I'm not completely hosed.   It broke howdy, got that semi working again.  it broke cursor (vscode clone ide), got that working again.  It didn't break windows dual boot, not that I ever use it, but hate to throw away.  A couple of gui extensions no longer work, ohh well.  The sound volume goes nuts when switching between external hdmi monitor when coming back out of standby, maybe the sound had been switched to the laptop speakers during standby.  Some positive feedback, I did a new install of 24.04 on a different older spare laptop last week and it went fine, seems to work but I'm not actively using it just running folding at home and backing up files to it over network.

So my current problem, python. Please forgive me, this is an infrequent hobby not expertise, I'm only able to do this by using everyone else's expertise.

A python project is not working.  It uses ib-insync, lightweight-charts and a few dependencies to work with broker api, plotting & ordering.   It was using python3.11 venv, and 22.04 used 3.10 for the os.   Now I see 24.04 is using 3.12 for the os.    I learned before, don't try to change python version that the system is using, barely recovered from that last time... 

First,  recreated .venv with 3.12, with requirements.txt,  from command palette in cursor      some errors installing req.txt.   
    /homez/dklein/FiPy/tv_ib_ptl$  source ./.venv/bin/activate  
    (.venv) $ pip3 install -r requirements.txt


    issue coming from webview, cursor chat helped:  
    apt-get install libgtk-3-dev webkit2gtk-4.0-dev libwebkit2gtk-4.0-dev
       but 4.0 is now 4.1 which did install     still fails.

Assuming I give up on it working with python3.12,  I think I need to install python3.11, try to recreate what it used before, but keep 3.12 as the main python3?

In order to get 3.11, I try this, (to no avail) ```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo: unable to execute /usr/bin/add-apt-repository: No such file or directory
```

Hmm, what?  why is there no link from python3 to python3.12?  do I add that?  
How is it that a new released system won't run python or python3 command?
 ```
/usr/bin$ ls -la pyt*lrwxrwxrwx 1 root root       7 Jun 13  2023 python -> python3
-rwxr-xr-x 1 root root 8019136 Sep 11 10:17 python3.12
lrwxrwxrwx 1 root root      34 Sep 11 10:17 python3.12-config -> x86_64-linux-gnu-python3.12-config
lrwxrwxrwx 1 root root      17 Aug  7 13:44 python3-config -> python3.12-config
dklein@MelbaToast:/usr/bin$ python3
bash: /usr/lib/command-not-found: cannot execute: required file not found

```

Maybe my state is due to what was set up before, here's what update-alternatives said when first run under 24.04.
```
$ sudo update-alternatives --config python3update-alternatives: warning: alternative /usr/bin/python3.10 (part of link group python3) doesn't exist; removing from list of alternatives
update-alternatives: warning: alternative /usr/bin/python3.11 (part of link group python3) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/python3 is dangling; it will be updated with best choice
There is no program which provides python3.
Nothing to configure.

[COLOR=#CCCCCC][FONT=system-ui]$ lsb_release -aNo LSB modules are available.Distributor ID:	UbuntuDescription:	Ubuntu 24.04.1 LTSRelease:	24.04Codename:	noble[/FONT][/COLOR]



```

---

### Post by daklein on 2024-10-17
next shot at it:   fix link to python, python3
```
dklein@MelbaToast:/usr/bin$ sudo ln -s /usr/bin/python3.12 /usr/bin/python3
[sudo] password for dklein: 
dklein@MelbaToast:/usr/bin$ ls -la pyt*
lrwxrwxrwx 1 root root       7 Jun 13  2023 python -> python3
lrwxrwxrwx 1 root root      19 Oct 17 14:49 python3 -> /usr/bin/python3.12
-rwxr-xr-x 1 root root 8019136 Sep 11 10:17 python3.12
lrwxrwxrwx 1 root root      34 Sep 11 10:17 python3.12-config -> x86_64-linux-gnu-python3.12-config
lrwxrwxrwx 1 root root      17 Aug  7 13:44 python3-config -> python3.12-config
dklein@MelbaToast:/usr/bin$ python
Python 3.12.3 (main, Sep 11 2024, 14:17:37) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()



```

Then try again with a python3.12 venv, shows the webview error.  Maybe this item is not compatible with python3.12?
```
dklein@MelbaToast:/homez/dklein/FiPy/tv_ib_ptl$ python3 -m venv .venv312dklein@MelbaToast:/homez/dklein/FiPy/tv_ib_ptl$ ./.venv312/bin/activate
bash: ./.venv312/bin/activate: Permission denied
dklein@MelbaToast:/homez/dklein/FiPy/tv_ib_ptl$ source ./.venv312/bin/activate
(.venv312) dklein@MelbaToast:/homez/dklein/FiPy/tv_ib_ptl$ pip3 install -r requirements.txt
Collecting lightweight-charts (from -r requirements.txt (line 1))
  Using cached lightweight_charts-2.1-py3-none-any.whl.metadata (8.0 kB)
Collecting pandas_ta (from -r requirements.txt (line 2))
  Using cached pandas_ta-0.3.14b.tar.gz (115 kB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Collecting TA-Lib (from -r requirements.txt (line 3))
  Using cached TA-Lib-0.4.32.tar.gz (368 kB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Collecting ib_insync (from -r requirements.txt (line 4))
  Using cached ib_insync-0.9.86-py3-none-any.whl.metadata (5.4 kB)
Collecting nest_asyncio (from -r requirements.txt (line 5))
  Using cached nest_asyncio-1.6.0-py3-none-any.whl.metadata (2.8 kB)
Collecting PyGObject (from -r requirements.txt (line 6))
  Using cached pygobject-3.50.0.tar.gz (1.1 MB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Installing backend dependencies ... done
  Preparing metadata (pyproject.toml) ... done
Collecting qtpy (from -r requirements.txt (line 7))
  Using cached QtPy-2.4.1-py3-none-any.whl.metadata (12 kB)
Collecting PyQtWebEngine (from -r requirements.txt (line 8))
  Using cached PyQtWebEngine-5.15.7-cp38-abi3-manylinux_2_17_x86_64.whl.metadata (1.8 kB)
Collecting pyarrow (from -r requirements.txt (line 9))
  Using cached pyarrow-17.0.0-cp312-cp312-manylinux_2_28_x86_64.whl.metadata (3.3 kB)
Collecting pandas (from -r requirements.txt (line 10))
  Using cached pandas-2.2.3-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (89 kB)
Collecting webview (from -r requirements.txt (line 11))
  Using cached webview-0.1.5.tar.gz (18 kB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... error
  error: subprocess-exited-with-error
  
  × Getting requirements to build wheel did not run successfully.
  &#9474; exit code: 1
  &#9584;&#9472;> [26 lines of output]
      Traceback (most recent call last):
        File "/homez/dklein/FiPy/tv_ib_ptl/.venv312/lib/python3.12/site-packages/pip/_vendor/pyproject_hooks/_in_process/_in_process.py", line 353, in <module>
          main()
        File "/homez/dklein/FiPy/tv_ib_ptl/.venv312/lib/python3.12/site-packages/pip/_vendor/pyproject_hooks/_in_process/_in_process.py", line 335, in main
          json_out['return_val'] = hook(**hook_input['kwargs'])
                                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
        File "/homez/dklein/FiPy/tv_ib_ptl/.venv312/lib/python3.12/site-packages/pip/_vendor/pyproject_hooks/_in_process/_in_process.py", line 118, in get_requires_for_build_wheel
          return hook(config_settings)
                 ^^^^^^^^^^^^^^^^^^^^^
        File "/tmp/pip-build-env-4yajo3fu/overlay/lib/python3.12/site-packages/setuptools/build_meta.py", line 332, in get_requires_for_build_wheel
          return self._get_build_requires(config_settings, requirements=[])
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
        File "/tmp/pip-build-env-4yajo3fu/overlay/lib/python3.12/site-packages/setuptools/build_meta.py", line 302, in _get_build_requires
          self.run_setup()
        File "/tmp/pip-build-env-4yajo3fu/overlay/lib/python3.12/site-packages/setuptools/build_meta.py", line 516, in run_setup
          super().run_setup(setup_script=setup_script)
        File "/tmp/pip-build-env-4yajo3fu/overlay/lib/python3.12/site-packages/setuptools/build_meta.py", line 318, in run_setup
          exec(code, locals())
        File "<string>", line 43, in <module>
        File "<string>", line 37, in pkgconfig
        File "/usr/lib/python3.12/subprocess.py", line 466, in check_output
          return run(*popenargs, stdout=PIPE, timeout=timeout, check=True,
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
        File "/usr/lib/python3.12/subprocess.py", line 571, in run
          raise CalledProcessError(retcode, process.args,
      subprocess.CalledProcessError: Command 'pkg-config --cflags gtk+-3.0 webkit2gtk-4.0' returned non-zero exit status 1.
      [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: subprocess-exited-with-error


× Getting requirements to build wheel did not run successfully.
&#9474; exit code: 1
&#9584;&#9472;> See above for output.


note: This error originates from a subprocess, and is likely not a problem with pip.
```

```
dklein@MelbaToast:~$ sudo apt-get install libgtk-3-dev webkit2gtk-4.0-dev libwebkit2gtk-4.0-devReading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package webkit2gtk-4.0-dev
E: Couldn't find any package by glob 'webkit2gtk-4.0-dev'
E: Couldn't find any package by regex 'webkit2gtk-4.0-dev'
E: Unable to locate package libwebkit2gtk-4.0-dev
E: Couldn't find any package by glob 'libwebkit2gtk-4.0-dev'
E: Couldn't find any package by regex 'libwebkit2gtk-4.0-dev'
dklein@MelbaToast:~$ sudo apt-get install libgtk-3-dev webkit2gtk-4.1-dev libwebkit2gtk-4.1-dev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libwebkit2gtk-4.1-dev' for regex 'webkit2gtk-4.1-dev'
libgtk-3-dev is already the newest version (3.24.41-4ubuntu1.2).
libwebkit2gtk-4.1-dev is already the newest version (2.44.3-0ubuntu0.24.04.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


Maybe I need to change somewhere to have it be using webkit2gtk-4.1 which is on the system, not 4.0  ?
Maybe I did that before to get it working with 3.11,   remember something like that, but dont' see in my notes.

---

### Post by daklein on 2024-10-17
fixed missing python, python3 link to python3.12

then solved further related issues from library version compatibility with python3.12,  thanks to cursor chat help:

chat suggested creating link to point  webview4.0 to installed 4.1 version
     sudo ln -s /usr/lib/x86_64-linux-gnu/pkgconfig/webkit2gtk-4.1.pc /usr/lib/x86_64-linux-gnu/pkgconfig/webkit2gtk-4.0.pc
    then install worked,                pip install --upgrade webview
    and then                              pip3 install -r requirements.txt
      
next error,  incompatible NumPy & TA-Lib packages.
    compile TA-Lib from source (did last time also)

then found that talib won't work with numpy > 2.0,  so 
    installed numpy 1.26.4,   seems to work with talib 0.4.32 & python3.12

a couple other minor changes and the python script works again, now in python3.12     Maybe that's progress...

Lesson learned, don't upgrade LTS ubunt unless I have to, even if the software updater keeps pestering me.

---

