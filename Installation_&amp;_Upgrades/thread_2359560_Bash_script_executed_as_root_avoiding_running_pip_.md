---
title: "Bash script executed as root: avoiding running pip as root"
date: 2017-04-25
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2017-04-25
Hi,
I have a question related to a bash script. I have a script that installs and updates the system and it requires root privileges.
However, since I also use pip to install several python packages with the following command:
```
pip install --user numpy scipy matplotlib ipython jupyter pandas sympy nose pyqt5
```
I get this warning:
```
The directory '/home/user/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
```
I can run the same command with sudo -H, nevertheless it [is not recommend]("https://stackoverflow.com/questions/21055859/what-are-the-risks-of-running-sudo-pip") to run pip with sudo.
So, how can I run a script with sudo and exclude the row with pip command?
Thank you

---

### Post by Keith_Helms on 2017-04-25
Just stick sudo in the script in front of whichever commands need it and then run the script without sudo.  You will be prompted to enter your password once the script hits a command that has sudo in front of it.

---

### Post by sisco311 on 2017-04-26
You can use sudo to run a command as another user:
```
sudo -H -u user pip ...
```

---

### Post by erotavlas on 2017-04-26
> **Keith_Helms said:**
> Just stick sudo in the script in front of  whichever commands need it and then run the script without sudo.  You  will be prompted to enter your password once the script hits a command  that has sudo in front of it.

I cannot follow this way since the update of the packages or the upgrade of the system require enough time and it prompts me a sudo password each time.

> **sisco311 said:**
> You can use sudo to run a command as another user:
```
sudo -H -u user pip ...
```

Ok this solution could work. However, I get different output by running:
```
sudo -H -u user pip install --user numpy scipy matplotlib ipython jupyter pandas sympy nose pyqt5
```

```
Requirement already up-to-date: pip in /home/user/.local/lib/python2.7/site-packages
Requirement already satisfied: numpy in /home/user/.local/lib/python2.7/site-packages
Collecting scipy
  Using cached scipy-0.19.0-cp27-cp27mu-manylinux1_x86_64.whl
Collecting matplotlib
  Using cached matplotlib-2.0.0-1-cp27-cp27mu-manylinux1_x86_64.whl
Requirement already satisfied: ipython in /usr/lib/python2.7/dist-packages
Collecting jupyter
  Using cached jupyter-1.0.0-py2.py3-none-any.whl
Collecting pandas
  Using cached pandas-0.19.2-cp27-cp27mu-manylinux1_x86_64.whl
Collecting sympy
  Using cached sympy-1.0.tar.gz
Collecting nose
  Using cached nose-1.3.7-py2-none-any.whl
Collecting pyqt5
  Could not find a version that satisfies the requirement pyqt5 (from versions: )
No matching distribution found for pyqt5
```

and
```
pip install --user numpy scipy matplotlib ipython jupyter pandas sympy nose pyqt5
```

```

Requirement already satisfied: numpy in /home/user/miniconda3/lib/python3.5/site-packages
Requirement already satisfied: scipy in /home/user/.local/lib/python3.5/site-packages
Requirement already satisfied: matplotlib in /home/user/.local/lib/python3.5/site-packages
Requirement already satisfied: ipython in /home/user/.local/lib/python3.5/site-packages
Requirement already satisfied: jupyter in /home/user/.local/lib/python3.5/site-packages
Requirement already satisfied: pandas in /home/user/.local/lib/python3.5/site-packages
Requirement already satisfied: sympy in /home/user/miniconda3/lib/python3.5/site-packages
Requirement already satisfied: nose in /home/user/miniconda3/lib/python3.5/site-packages
Requirement already satisfied: pyqt5 in /home/user/miniconda3/lib/python3.5/site-packages
Requirement already satisfied: python-dateutil in /home/user/.local/lib/python3.5/site-packages (from matplotlib)
Requirement already satisfied: cycler>=0.10 in /home/user/.local/lib/python3.5/site-packages (from matplotlib)
Requirement already satisfied: pyparsing!=2.0.0,!=2.0.4,!=2.1.2,!=2.1.6,>=1.5.6 in /home/user/miniconda3/lib/python3.5/site-packages (from matplotlib)
Requirement already satisfied: pytz in /home/user/.local/lib/python3.5/site-packages (from matplotlib)
Requirement already satisfied: six>=1.10 in /home/user/miniconda3/lib/python3.5/site-packages (from matplotlib)
Requirement already satisfied: setuptools>=18.5 in /home/user/miniconda3/lib/python3.5/site-packages/setuptools-27.2.0-py3.5.egg (from ipython)
Requirement already satisfied: traitlets>=4.2 in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: simplegeneric>0.8 in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: decorator in /home/user/miniconda3/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: pexpect; sys_platform != "win32" in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: jedi>=0.10 in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: prompt-toolkit<2.0.0,>=1.0.4 in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: pickleshare in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: pygments in /home/user/.local/lib/python3.5/site-packages (from ipython)
Requirement already satisfied: ipywidgets in /home/user/.local/lib/python3.5/site-packages (from jupyter)
Requirement already satisfied: notebook in /home/user/.local/lib/python3.5/site-packages (from jupyter)
Requirement already satisfied: nbconvert in /home/user/.local/lib/python3.5/site-packages (from jupyter)
Requirement already satisfied: qtconsole in /home/user/.local/lib/python3.5/site-packages (from jupyter)
Requirement already satisfied: jupyter-console in /home/user/.local/lib/python3.5/site-packages (from jupyter)
Requirement already satisfied: ipykernel in /home/user/.local/lib/python3.5/site-packages (from jupyter)
Requirement already satisfied: mpmath>=0.19 in /home/user/miniconda3/lib/python3.5/site-packages (from sympy)
Requirement already satisfied: sip<4.20,>=4.19 in /home/user/miniconda3/lib/python3.5/site-packages (from pyqt5)
Requirement already satisfied: ipython-genutils in /home/user/.local/lib/python3.5/site-packages (from traitlets>=4.2->ipython)
Requirement already satisfied: ptyprocess>=0.5 in /home/user/.local/lib/python3.5/site-packages (from pexpect; sys_platform != "win32"->ipython)
Requirement already satisfied: wcwidth in /home/user/.local/lib/python3.5/site-packages (from prompt-toolkit<2.0.0,>=1.0.4->ipython)
Requirement already satisfied: nbformat>=4.2.0 in /home/user/.local/lib/python3.5/site-packages (from ipywidgets->jupyter)
Requirement already satisfied: widgetsnbextension~=2.0.0 in /home/user/.local/lib/python3.5/site-packages (from ipywidgets->jupyter)
Requirement already satisfied: jupyter-core in /home/user/.local/lib/python3.5/site-packages (from notebook->jupyter)
Requirement already satisfied: tornado>=4 in /home/user/.local/lib/python3.5/site-packages (from notebook->jupyter)
Requirement already satisfied: terminado>=0.3.3; sys_platform != "win32" in /home/user/.local/lib/python3.5/site-packages (from notebook->jupyter)
Requirement already satisfied: jinja2 in /home/user/miniconda3/lib/python3.5/site-packages (from notebook->jupyter)
Requirement already satisfied: jupyter-client in /home/user/.local/lib/python3.5/site-packages (from notebook->jupyter)
Requirement already satisfied: testpath in /home/user/.local/lib/python3.5/site-packages (from nbconvert->jupyter)
Requirement already satisfied: pandocfilters>=1.4.1 in /home/user/.local/lib/python3.5/site-packages (from nbconvert->jupyter)
Requirement already satisfied: bleach in /home/user/miniconda3/lib/python3.5/site-packages (from nbconvert->jupyter)
Requirement already satisfied: entrypoints>=0.2.2 in /home/user/.local/lib/python3.5/site-packages (from nbconvert->jupyter)
Requirement already satisfied: mistune!=0.6 in /home/user/.local/lib/python3.5/site-packages (from nbconvert->jupyter)
Requirement already satisfied: jsonschema!=2.5.0,>=2.4 in /home/user/.local/lib/python3.5/site-packages (from nbformat>=4.2.0->ipywidgets->jupyter)
Requirement already satisfied: MarkupSafe>=0.23 in /home/user/miniconda3/lib/python3.5/site-packages (from jinja2->notebook->jupyter)
Requirement already satisfied: pyzmq>=13 in /home/user/.local/lib/python3.5/site-packages (from jupyter-client->notebook->jupyter)
Requirement already satisfied: html5lib>=0.99999999 in /home/user/miniconda3/lib/python3.5/site-packages (from bleach->nbconvert->jupyter)
Requirement already satisfied: webencodings in /home/user/miniconda3/lib/python3.5/site-packages (from html5lib>=0.99999999->bleach->nbconvert->jupyter)

```


Do you confirm that the two options are equal in terms of results?
It do not seem so.

Thank you

---

