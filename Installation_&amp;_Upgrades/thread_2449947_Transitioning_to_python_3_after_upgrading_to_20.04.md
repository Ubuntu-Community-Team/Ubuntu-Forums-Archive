---
title: "Transitioning to python 3 after upgrading to 20.04"
date: 2020-09-04
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2020-09-04
I upgraded my installation of Ubuntu from 18.04 to 20.04 and now I want to make Python 3 the default. I also want pip to default to the python 3 version. Are there instructions I could follow?

---

### Post by CelticWarrior on 2020-09-04
Python3 should be the default already.

---

### Post by monkeybrain20122 on 2020-09-05
> **CelticWarrior said:**
> Python3 should be the default already.

Not really. On my 20.04 laptop
```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

~$ which python
/usr/bin/python

~$ python --version
Python 2.7.18rc1

```

pip is kind of inconsistent in that the default pip is decided by the last time you upgraded pip with pip (but if you never use pip to upgrade pip, i.e, straight from the repo, then pip == pip2)

so e.g if the last time you upgraded pip with
```

sudo pip3 install -U pip
```

then next time when you use pip it would be assumed to mean pip3, to invoke pip2 you will have to say "pip2" explicitly.

if you followed the above by updating pip2
```

sudo pip2 install -U pip
```

Then the next time you invoke pip it will automatically assumed to be pip2, and to use pip3 it will have to be invoked explicitly as "pip3".

---

### Post by monkeybrain20122 on 2020-09-05
I don't think it is a good idea to mess with default python configuration or version because then some of your system components will stop working.

Personally I don't recommend using system python for development or installing  python modules (e.g numpy) from apt (they are outdated for one thing) For development you need flexibility to upgrade or downgrade modules or maybe compiling from source and it creates confusions (if not instability) if you mix these customizations with the system, and finally there is no reason why one would need sudo to install these local modifications systemwide (though that can be avoided with pip install --user)

Instead try to either 1) use conda or 2) set up virtualenv or 3) install python locally and set up a local development environment. None of these options need sudo and all safely separated from system's python. These are listed with increasing degrees of difficulty, i.e conda is the easiest, the catch is it pulls in dependencies that may not really be needed and the version control may be too rigid, option 3) is most flexible and streamlined but needs a bit more experience to set up.

---

### Post by hojjat on 2020-09-07
> **monkeybrain20122 said:**
> Instead try to either 1) use conda or 2) set up virtualenv or 3) install python locally and set up a local development environment. None of these options need sudo and all safely separated from system's python. These are listed with increasing degrees of difficulty, i.e conda is the easiest, the catch is it pulls in dependencies that may not really be needed and the version control may be too rigid, option 3) is most flexible and streamlined but needs a bit more experience to set up.

Of these, I like option 3 the most. Do you know of any link to instructions on how best to do it?

---

### Post by monkeybrain20122 on 2020-09-08
> **hojjat said:**
> Of these, I like option 3 the most. Do you know of any link to instructions on how best to do it?

I don't know any link, but I can give you the instructions since this is what I do.

to prepare, get the build tools

```
sudo apt install build-essential autoconf
```

Then get the dependencies
```

sudo apt build-dep python3
```

Get python from [here]("https://www.python.org/") and install it, e.g I installed python3.8.5 in the folder $HOME/opt/python385 so, the compiling process looks like
```

./configure --prefix=$HOME/opt/python385

make -j4

make check -j4

make install
```



You can add other options after ./configure,  to see the options, type

```
./configure --help
```

optional: Instead of typing pip3 and python3 I went to the bin subdirectory of the python install (in my case $HOME/opt/python385/bin) and made  symlinks python to python3 and pip to pip3

e.g 
```
ln -s /home/monkeybrain/opt/python385/bin/python3 /home/monkeybrain/opt/python385/bin/python
```
```
ln -s /home/monkeybrain/opt/python385/bin/pip3 /home/monkeybrain/opt/python385/bin/pip
```

Now to work with your installed version of python you need to set a bunch environmental variables, I put them in a script so every time I run python I just have to source the script first. e.g my script is in ~/Scripts/python385.conf. I have to source the script before invoking python
```
$ source ~/Scripts/python385.conf

$ which python
/home/monkeybrain/opt/python385/bin/python

$ python
Python 3.8.5 (default, Aug 21 2020, 18:27:22) 
[GCC 9.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

Note in the above I just type python instead of python3 because of the symlink I created. Likewise pip install is the same as pip3 install

Here is my python385.conf, sourced above before invoking python
```

export PREFIX=/home/monkeybrain/opt/python385
export HOME=$PREFIX
export PATH=$PREFIX/bin:$PATH
export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH
export PYTHONUSERBASE=$PREFIX
export PYTHONPATH=$PREFIX/lib/python38/site-packages:$PYTHONPATH
```

export HOME is optional (this changes your $HOME directory) I have different pythons and I use spyder so I prefer a .config for each python, spyder is supposed to work with multiple pythons but  I can't make it work that way, so I installed spyder for each python. You may find the same device useful for other applications that you want to have a separate .config file.

$PYTHONUSERBASE may not be necessary, it specifies where pip will install modules if you use the --user flag. It is useful if you use system python and you want to install python modules in a non standard directory, one reason is to avoid needing sudo for pip install (if use system python and without explicitly exporting PYTHONUSERBASE, pip install --user will install in ~/.local/lib/pythonxy/site-packages) But in our set up you don't need sudo anyway so there is no need for the --user flag

---

### Post by monkeybrain20122 on 2020-09-08
The above set up is what I use, but before you do that, keep in mind that a lot of tutorials and installation guides (e.g a lot of machine learning stuffs like pytorch or mxnet if you want gpu support) are written with conda in mind, it is not difficult to adopt those for the setup above, but you'll need to make modifications to those instructions as needed and often would involve more works e.g you might have to compile dependencies from source but conda will have them packaged already..  

In general the setup above is convenient if you compile from source a lot but it is a hassle if you don't like compiling (and having a fast and powerful machine is a must if you compile from source often)

So weigh your options carefully, for convenience conda is recommended.

---

