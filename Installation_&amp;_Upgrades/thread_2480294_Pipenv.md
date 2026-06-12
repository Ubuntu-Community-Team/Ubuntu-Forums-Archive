---
title: "Pipenv"
date: 2022-10-24
forum: Installation &amp; Upgrades
---

### Post by akivan on 2022-10-24
I have installed pip via the "[get-pip.py]("https://pip.pypa.io/en/stable/installation/")" and via apt. Also install the "pipenv" using pip and pip3. Same problem how ever im installing it. 


But when i create the environment using **pipenv install** the environment is created ok but when i try to install some library it's using the host pip and libraries are installed on the host path not on the environment itself.

Example: I'm installing the lib requests and nothing from files are in the environment path. And when i try to import the module its says its missing. But on the host machine the module is there. 


&#10140;  Test pipenv shell
Launching subshell in virtual environment...
&#10140;  Test  . /home/user1/.local/share/virtualenvs/Test-f3UeTgqf/bin/activate
(Test-f3UeTgqf) &#10140;  Test 
(Test-f3UeTgqf) &#10140;  Test which pip
/home/user1/.local/bin/pip
(Test-f3UeTgqf) &#10140;  Test which pip3
/home/user1/.local/bin/pip3
(Test-f3UeTgqf) &#10140;  Test 

why which is pointing to the host path of the pip, should it this be from the virtual environment path? Could this be the problem of why libraries are not install in the environment?

Updates
Crating pipenv logs
WARNING: --three is deprecated! pipenv uses python3 by default
Creating a virtualenv for this project...
Pipfile: /home/ivan/Projects/Test/Pipfile
Using /usr/bin/python3 (3.10.6) to create virtualenv...
&#10296; Creating virtual environment...created virtual environment CPython3.10.6.final.0-64 in 105ms
  creator Venv(dest=/home/ivan/.local/share/virtualenvs/Test-f3UeTgqf, clear=False, no_vcs_ignore=False, global=False, describe=CPython3Posix)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/ivan/.local/share/virtualenv)
    added seed packages: pip==22.2.2, setuptools==65.4.1, wheel==0.37.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator


&#10004; Successfully created virtual environment! 
Virtualenv location: /home/ivan/.local/share/virtualenvs/Test-f3UeTgqf
Creating a Pipfile for this project...
Pipfile.lock not found, creating...
Locking [packages] dependencies...
Locking [dev-packages] dependencies...
Updated Pipfile.lock (2ac81ce11198646f581b04616654f2ec6cd1f7a2c54081f2e3aecba53449386d)!
Installing dependencies from Pipfile.lock (49386d)...
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.

---

