---
title: "ruby and rails and stuff"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-08-19
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

im installing the latest rails....  check it out

start from scratch start from source

nab this file in your browser [ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.gz](ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.gz)

```

sudo apt-get install libyaml-dev sqlite3 nodejs
cd $HOME/Downloads
wget ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.gz
tar -xf ruby*
cd ruby*

```

per LFS instructions

```

./configure --prefix=/usr \
            --enable-shared \
            --enable-pthread \
            --enable-install-doc &&
make

```

then probably a

```

sudo make install

```

all is well &&

```

sudo gem update --system

```

&&

```

sudo gem install rdoc
sudo gem install rdoc-data
sudo gem install rails

```

to get a project up quickly

```

sudo mkdir /var/www/ror
cd /var/www
sudo rails new ror/
cd /var/www/ror
sudo bundle install
rails server -d

```

then point your browser @ [127.0.0.1:3000](127.0.0.1:3000)


"sudo gem update --system
Latest version currently installed. Aborting."

not "debian specific locked useless gem management system"

[http://railscasts.com/episodes/265-rails-3-1-overview?autoplay=true](http://railscasts.com/episodes/265-rails-3-1-overview?autoplay=true) presented me a problem i would like to solve while im at it.  im going to install the "rvm" command for version control of ruby, and another page gave me the idea to use version control with git.  these are new ideas to me, web dev is new to me.  i will install this system wide.

need to setup some environment stuff


```

sudo su

```

```

export rvm_path=/usr/rvm
bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)

```

remove this problematic script and replace it with a better one

```

sudo su

```

```

rm /usr/rvm/scripts/rvm
cat > /usr/rvm/scripts/rvm << "EOF"
#!/usr/bin/env bash

# rvm : Ruby enVironment Manager
# https://rvm.beginrescueend.com
# https://github.com/wayneeseguin/rvm

# Is RVM loaded as a shell function already?

export HOME="${HOME%%+(\/)}" # Remove trailing slashes if they exist on HOME

if (( ${rvm_ignore_rvmrc:=0} == 0 ))
then
  for rvmrc in /etc/rvmrc "$HOME/.rvmrc"
  do
    if [[ -f "$rvmrc" ]]
    then
      if \grep '^\s*rvm .*$' "$rvmrc" >/dev/null 2>&1
      then
        printf "\nError:
        $rvmrc is for rvm settings only.
        rvm CLI may NOT be called from within $rvmrc.
        Skipping the loading of $rvmrc"
        return 1
      else
        source "$rvmrc"
      fi
    fi
  done
fi

#if [[ -z "${rvm_path:-}" ]]
#then
  # Set the default sandboxed value.
  # TODO: Alter the variable names to make sense
  if [[ -z "${rvm_user_install_flag:-}" ]]
  then
    if (( UID == 0 )) ||
      [[ -n "${rvm_prefix:-}" && "${rvm_prefix:-}" != "${HOME}" ]]
    then
      rvm_user_install_flag=0
    else
      rvm_user_install_flag=1
    fi
  fi

  if [[ -z "${rvm_prefix:-}" ]]
  then
    true ${rvm_user_install_flag:=0}
    if (( UID > 0 || rvm_user_install_flag == 1 ))
    then
      rvm_prefix="/usr"
    else
      rvm_prefix="/usr"
    fi
  fi

  true "${rvm_prefix/rvm/scripts}" # Fix rvm_prefix changes, older installs.

  if [[ -z "${rvm_path:-}" ]]
  then
    if [[ "$rvm_prefix" = "$HOME" ]]
    then
      rvm_path="${rvm_prefix}/.rvm"
    else
      rvm_path="${rvm_prefix}/rvm"
    fi
  fi
#fi
\export rvm_prefix
\export rvm_user_install_flag
\export rvm_path="${rvm_path%%+(\/)}"

if [[ -n "${BASH_VERSION:-}" ]]
then
  if type rvm 2>&1 | \grep 'function' >/dev/null
  then
    rvm_loaded_flag=1
  else
    rvm_loaded_flag=0
  fi
elif [[ -n "${ZSH_VERSION:-}" ]]
then
  if type rvm 2>&1 | \grep 'function' >/dev/null
  then
    rvm_loaded_flag=1
  else
    rvm_loaded_flag=0
  fi
else
  rvm_loaded_flag=0
fi

if (( ${rvm_loaded_flag:=0} == 0 )) || (( ${rvm_reload_flag:=0} == 1 ))
then
  if [[ -n "${rvm_path}" && -d "$rvm_path" ]]
  then
    true ${rvm_scripts_path:="$rvm_path/scripts"}

    for script in base version selector cd cli override_gem
    do
      if [[ -f "$rvm_scripts_path/$script" ]]
      then
        source "$rvm_scripts_path/$script"
      else
        printf "WARNING:
        Could not source '$rvm_scripts_path/$script' as file does not exist.
        RVM will likely not work as expected.\n"
      fi
    done

    rvm_version="$(cat "$rvm_path/VERSION")"

    export rvm_version="${rvm_version/%.}"

    alias rvm-restart="rvm_reload_flag=1 source '${rvm_path}/scripts/rvm'"

    if ! command -v ruby >/dev/null 2>&1 || command -v ruby | \grep -v rvm >/dev/null
    then
      if [[ -s "$rvm_path/environments/default" ]]
      then
        source "$rvm_path/environments/default"
      fi
    fi

    # Makes sure rvm_bin_path is in PATH atleast once.
    __rvm_conditionally_add_bin_path

    if (( ${rvm_reload_flag:=0} == 1 ))
    then
      printf 'RVM reloaded!\n'
    fi

    rvm_loaded_flag=1
    rvm_reload_flag=0
  else
    printf "\n\$rvm_path ($rvm_path) does not exist."
  fi
  unset rvm_prefix_needs_trailing_slash rvm_rc_files rvm_gems_cache_path \
    rvm_gems_path rvm_project_rvmrc_default rvm_gemset_separator
fi

if [[ -t 0 ]] && command -v __rvm_project_rvmrc >/dev/null  2>&1
then
  # Reload the rvmrc, use promptless ensuring shell processes does not
  # prompt if .rvmrc trust value is not stored.
  rvm_promptless=1 __rvm_project_rvmrc
fi
EOF

```


and then add the RVM to environment && run once as sudo su also to install for root

```

cat >> $HOME/.bashrc << "EOF"
[[ -s "/usr/rvm/scripts/rvm" ]] && source "/usr/rvm/scripts/rvm" #Load RVM into a shell session *as a function*
EOF

```

gedit /usr/rvm/scripts/rvm to set its path from $HOME to /usr, and also from /usr/local to /usr

open a new shell or run

```

source .bashrc

```

now test
```

type rvm | head -1

```

and we want it to return "rvm is a function."

rvm is a function

now ready to use RVM as this mac ruby tutorial requires.
im only going to use sudo su for RVM as its a broken / quick dirty fix that i scripted in.  it might be broken further down the line but ill test.  lol its probably broken down the line, ill return to refine and fix it eventually, but since sudo su root using commands works for RVM ill be a root warior for a minute....

get root
```

sudo su

```
punish your root terminal with this voodoo **** storm

```

rvm get head
rvm reload
rvm install 1.8.7
rvm install 1.9.2
rvm --create 1.8.7-p302@ror2
rvm --create use 1.9.2@ror3
rvm --default use 1.9.2@ror3
gem update --system 1.8.5
gem update --system
bundle install
gem install sqlite3-ruby
gem install rdoc
gem install rdoc-data
gem install rails
exit

```

which rails

rails new ror/ as previously done before to get the system up and running.

finishing touches

```

sudo rm -rf $HOME/Downloads/ruby*

```


a few tutorials i have seen suggest installing git, so ill follow [http://ruby.railstutorial.org/ruby-on-rails-tutorial-book#sec:rubygems](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book#sec:rubygems) for a moment

[IMG]http://img827.imageshack.us/img827/146/ubuntua.jpg[/IMG]

this tutorial is probably a good idea to run also......
[http://vimeo.com/369095](http://vimeo.com/369095)


and now that we have that all lined up, now for some rails 3 videos =D  wtf is a rail????
[http://rubyonrails.org/screencasts/rails3/](http://rubyonrails.org/screencasts/rails3/)


gmate....  gives me problems....

```

sudo apt-get install gedit-plugins

```

install a terminal in ur gedit ;-)

```

sudo apt-get install python-webkit-dev python-pyinotify ack-grep

```

continue nabbing goodies from...

[https://github.com/gmate/gmate](https://github.com/gmate/gmate)

and then write how to do passenger deploy with apache....

nabbed from here....

[http://modrails.com/](http://modrails.com/)

looks like need to do this 4 passenger

```

sudo apt-get install apache2-threaded-dev

```

MOAR

```

sudo su

```

```

cat >> /etc/apache2/httpd.conf << EOF
LoadModule passenger_module /usr/lib/ruby/gems/1.9.1/gems/passenger-3.0.11/ext/apache2/mod_passenger.so
PassengerRoot /usr/lib/ruby/gems/1.9.1/gems/passenger-3.0.11
PassengerRuby /usr/bin/ruby
<VirtualHost *:82>
DocumentRoot /var/www/ror
</VirtualHost>
EOF

```

MOAR

```

cat >> /etc/apache2/ports.conf << EOF
NameVirtualHost *:82
Listen 82
EOF
exit

```

now localhost:82 should be your passenger deploy

---

