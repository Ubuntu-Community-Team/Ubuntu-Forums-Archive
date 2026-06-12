---
title: "Install wiki moin moinmoin on 5.05-6.06"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by AllBuntu on 2006-06-30
So, there is a wiki with 5.05/6.06 though nobody cared for explaining how to make it work! At least, it's been that way until now:

If you want to host your own wiki and has Ubuntu installed, follow the below steps (moin is what ubuntu.com uses for Wiki):
Skill level: know your way around bash

1. Install
sudo apt-get install python2.4-moinmoin
sudo apt-get install apache2

2. Create your own wiki called mywiki
cd /usr/share/moin
sudo mkdir mywiki
sudo cp -R data mywiki
sudo cp -R underlay mywiki
sudo cp server/moin.cgi mywiki
sudo chown www-data.www-data mywiki
sudo chmod -R ug+rwX mywiki
sudo chmod -R o-rwx mywiki

3. Commission moin to find your new wiki
cd /etc/moin
sudo cp moinmaster.py mywiki.py

insert into farmconfig.py, on a line after "wikis = ["
   ("mywiki",  r".*"),

in mywiki.py change the data_dir line to
  data_dir = '/usr/share/moin/mywiki/data'

4. Make apache ready for your wiki
insert into /etc/apache2/sites-available/default
(inside of the "<VirtualHost *>" tag)

### moin
  ScriptAlias /mywiki "/usr/share/moin/mywiki/moin.cgi"
  alias /wiki "/usr/share/moin/htdocs"
  <Directory /usr/share/moin/htdocs>
    Order allow,deny
    allow from all
  </Directory>
### end moin

sudo /etc/init.d/apache2 restart

5. See if it works
[http://127.0.0.1/mywiki](http://127.0.0.1/mywiki)

(they also have a test command)
[http://127.0.0.1/mywiki?action=test](http://127.0.0.1/mywiki?action=test)

Once it works, I am sure you can fix tons of stuff such as style it like the Ubuntu wiki, add ssl and digest authentication, use another name or another directory etcetera. After all, that's why we use Ubuntu!

And, if you happen to be one of those Python-high writers of moin, please get an apache-integrated ready-to-go wiki into the package, will you?

---

### Post by felipe_alfaro on 2006-06-30
3. cd /etc/moin
4. sudo cp moinmaster.py mywiki.py

I don't have such a file named /etc/moin/moinmaster.py. All I've got is:

/etc/moin/farmconfig.py
/etc/moin/mywiki.py

Any ideas?

---

### Post by Petrush on 2006-07-01
I think it should be:
sudo chown -R www-data.www-data mywiki

I used the mywiki.py file in /etc/moin instead of moinmaster.

Works! Thanks!

---

### Post by ubuntu_demon on 2006-09-25
> **Petrush said:**
> I think it should be:
sudo chown -R www-data.www-data mywiki

I used the mywiki.py file in /etc/moin instead of moinmaster.

Works! Thanks!
indeed

Thanks AllBuntu and Petrush !

I don't think it was needed but I also changed data_dir in farmconfig.py :

```

    data_dir = '/usr/share/moin/mywiki/data'

```

---

### Post by funk19 on 2006-12-10
Hi guys,

I've searched everywhere:- Forums, MoinMoin, Google and alas I am having an install issue with moinmoin that is driving me insane.

I followed the following howtos down to the exact letter - changing nothing as I went along:

[http://moinmoin.wikiwikiweb.de/HelpOnInstalling/WikiInstanceCreation](http://moinmoin.wikiwikiweb.de/HelpOnInstalling/WikiInstanceCreation)
[http://moinmoin.wikiwikiweb.de/HelpOnInstalling/ApacheOnLinux](http://moinmoin.wikiwikiweb.de/HelpOnInstalling/ApacheOnLinux)

When I run [http://127.0.0.1/mywiki?action=test](http://127.0.0.1/mywiki?action=test) I am able to get to the what seems like the final stage of creating an instance but I get the following error:

KeyError 'wikiconfig'

On viewing the debug info here is the info pre-'wikiconfig' keyerror

```
 7.
/usr/lib/python2.4/site-packages/MoinMoin/multiconfig.py in _loadPluginModule (self=<MoinMoin.wikiconfig.Config instance>)
         1. 640 # Load the module and set in sys.modules
         2. 641 module = imp.load_module(name, fp, path, info)
         3. 642 sys.modules[self.siteid].plugin = module
         4. 643 finally:
         5. 644 # Make sure fp is closed properly
          * sys = <module 'sys' (built-in)>
          * sys.modules = {'Cookie': <module 'Cookie' from '/usr/lib/python2.4/Cookie.pyc'>, 'MoinMoin': <module 'MoinMoin' from '/usr/lib/python2.4/site-packages/MoinMoin/__init__.pyc'>, 'MoinMoin.Cookie': None, 'MoinMoin.MoinMoin': None, 'MoinMoin.StringIO': None, 'MoinMoin.__builtin__': None, 'MoinMoin.auth': <module 'MoinMoin.auth' from '/usr/lib/python2.4/site-packages/MoinMoin/auth.pyc'>, 'MoinMoin.cPickle': None, 'MoinMoin.cStringIO': None, 'MoinMoin.caching': <module 'MoinMoin.caching' from '/usr/lib/python2.4/site-packages/MoinMoin/caching.pyc'>, ...}
          * self = <MoinMoin.wikiconfig.Config instance>
          * self.siteid = 'wikiconfig'
          * ].plugin undefined
          * module = <module 'wikiconfig.plugin' from '/usr/share/moin/mywiki/data/plugin/__init__.pyc'>

KeyError

'wikiconfig'

    * args = ('wikiconfig',)
```

In looking at the multiconfig.py file after line 644 the following code seems to be where my system halts.

```
                        # Make sure fp is closed properly
                        if fp:
                            fp.close()
            finally:
                imp.release_lock()
        except ImportError, err:
            msg = '''
Could not import plugin package "%(path)s/plugin" because of ImportError:
%(err)s.

Make sure your data directory path is correct, check permissions, and
that the data/plugin directory has an __init__.py file.
''' % {'path': self.data_dir, 'err': str(err)}
            raise error.ConfigurationError(msg)

    def _fillDicts(self):
        """ fill config dicts

        Fills in missing dict keys of derived user config by copying
        them from this base class.
        """
        # user checkbox defaults
        for key, value in DefaultConfig.user_checkbox_defaults.items():
            if not self.user_checkbox_defaults.has_key(key):
                self.user_checkbox_defaults[key] = value

    def __getitem__(self, item):
        """ Make it possible to access a config object like a dict """
        return getattr(self, item)
    
# remove the gettext pseudo function 
del _
```

Has anyone got any ideas for me? I've honestly tried everything but this darn bugger won't work....

---

### Post by soro2005 on 2007-05-13
Old thread, but still very useful. Thanks a bunch! I was about to give up on trying to find my way through this, now it works! :)  On Feisty, by the way.

---

### Post by 4integration on 2007-08-20
Trying to get moinmoin to work on Kubuntu Feisty Fawn but having problems. I have followed the guide at [https://wiki.ubuntu.com/HelpOnInstalling](https://wiki.ubuntu.com/HelpOnInstalling)
I am not experienced in Python....

**Install the software:**
```
sudo apt-get install python2.4-moinmoin
sudo apt-get install apache2
```
**Creating a wiki directory with permissions:**
```

cd /usr/share/moin
sudo mkdir wiki.domain.se
sudo cp -R data wiki.domain.se
sudo cp -R underlay wiki.domain.se
sudo cp server/moin.cgi wiki.domain.se
sudo chown -R www-data.www-data wiki.domain.se
sudo chmod -R ug+rwx wiki.domain.se
sudo chmod -R o-rwx wiki.domain.se
```

**Configure moinmoin to find the wiki.**
Modify the line in* /etc/moin/farmconfig.py*
```
("mywiki", r".*"),
```
to
```
("wiki.domain.se", r".*"),
```

Copy the file:
```
sudo cp /etc/moin/mywiki.py /etc/moin/wiki.domain.se.py
```

Edit /etc/moin/wiki.domain.se.py
```
# -*- coding: iso-8859-1 -*-

from farmconfig import FarmConfig

class Config(FarmConfig):
    sitename = u'wiki.domain.se' # [Unicode]
    interwikiname = 'wiki.domain.se'
    page_front_page = u"FrontPage"
    data_dir = '/usr/share/moin/wiki.domain.se/data'
```

**Setup apache virtual host to find the wiki.**

```
# more /etc/apache2/sites-available/wiki.domain.se.conf
<VirtualHost *>
        ServerName wiki.domain.se
        DocumentRoot "/var/media/webroots/wiki.domain.se/web"
        <Directory "/var/media/webroots/wiki.domain.se/web">
                allow from all
                Options +Indexes
        </Directory>

        ### moin
        ScriptAlias /wikitest "/usr/share/moin/wiki.domain.se/moin.cgi"
        alias /wiki "/usr/share/moin/htdocs"
        <Directory /usr/share/moin/htdocs>
                Order allow,deny
                allow from all
        </Directory>
        ### end moin
</VirtualHost>

```

**_[COLOR="Red"]When browsing [http://wiki.domain.se/wikitest](http://wiki.domain.se/wikitest) I get this:[/COLOR]_**
```
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/MoinMoin/request.py", line 1376, in __init__
    RequestBase.__init__(self, properties)
  File "/var/lib/python-support/python2.5/MoinMoin/request.py", line 113, in __init__
    self._load_multi_cfg()
  File "/var/lib/python-support/python2.5/MoinMoin/request.py", line 261, in _load_multi_cfg
    self.cfg = multiconfig.getConfig(self.url)
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 154, in getConfig
    config = _makeConfig(configName)
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 109, in _makeConfig
    raise error.ConfigurationError(msg)
ConfigurationError: ImportError: No module named wiki.domain.se


Check that the file is in the same directory as the server script. If
it is not, you must add the path of the directory where the file is
located to the python path in the server script. See the comments at
the top of the server script.

Check that the configuration file name is either "wikiconfig.py" or the
module name specified in the wikis list in farmconfig.py. Note that the
module name does not include the ".py" suffix.

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 93, in _makeConfig
    module, mtime = _importConfigModule(name)
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 29, in _importConfigModule
    module = __import__(name, globals(), {})
ImportError: No module named wiki.domain.se

Additionally cgitb raised this exception:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/MoinMoin/failure.py", line 142, in handle
    handler = cgitb.Hook(file=request, display=request.cfg.show_traceback,
AttributeError: 'RequestCGI' object has no attribute 'cfg'

```

Any idea what's wrong??

---

### Post by 4integration on 2007-08-20
I think I solved it...

moinmoin or Python doesn't like wiki names as "wiki.domain.se" but "wiki_domain_se" seems to work

---

### Post by Dirren on 2007-09-10
Excellent initiative to document this!
I've tried to get the moin-wiki to work without using apache (had some nasty experiences trying to configure it before :) ), but no luck. 
Following this howto I've got the wiki working again. I did this on Feisty, so the procedure is still valid!

---

### Post by orengolan on 2007-12-09
I follow the steps and can't see the wiki when running apache.
here is the apache log file:

```

  File "/usr/share/moin/mywiki/moin.cgi", line 39, in <module>
    from MoinMoin.request import RequestCGI
ImportError: cannot import name RequestCGI
[Sun Dec 09 20:14:06 2007] [error] [client 127.0.0.1] Premature end of script headers: moin.cgi, referer: http://ubuntuforums.org/showthread.php?t=206853&highlight=moinmoin
[Sun Dec 09 20:14:06 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

```

any ideas?

---

### Post by joejk2 on 2008-02-09
Many thanks for this post!

Found things slightly different under 7.10 Gutsy Gibbon:

Although 'mywiki.py' and 'farmconfig.py' still exist under /etc/moin  they don't seem to do anything anymore.  

Instead I had to edit 'mywiki.py' and 'farmconfig.py' under /usr/share/moin/config/wikifarm

---

### Post by joejk2 on 2008-02-09
.... and I had to edit data_dir and data_underlay_dir in /usr/share/moin/config/wikiconfig.py ...
Joe

---

