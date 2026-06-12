---
title: "Problems with qt and Tk modules after upgrading to python2.5"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by otakuj462 on 2007-07-09
Hi, I've recently upgraded to python2.5 by using apt-get. Unfortunately, I cannot get python2.5 to import the libraries _tkinter or qt. This has broken several of the applications I typically use, including guidance-power-manager. 
The python website has some advice on debugging the Tkinter issue:
> Step 1 - can _tkinter be imported?

Try the following command at the Python prompt:

>>> import _tkinter # with underscore, and lowercase 't'

...
    * If it fails with "No module named _tkinter", your Python configuration needs to be modified to include this module (which is an extension module implemented in C). Do **not** edit Modules/Setup (it is out of date). You may have to install Tcl and Tk (when using RPM, install the -devel RPMs as well) and/or edit the setup.py script to point to the right locations where Tcl/Tk is installed. If you install Tcl/Tk in the default locations, simply rerunning "make" should build the _tkinter extension.

Unfortunately, running "make" on the python2.5 source doesn't seem like a very "debian" way to fix this problem. 
I have python2.5-dev installed. Also, here is what I have in my /usr/lib/python2.5 directory:
```
aifc.py              httplib.py             sha.pyc
aifc.pyc             httplib.pyc            shelve.py
anydbm.py            idlelib                shelve.pyc
anydbm.pyc           ihooks.py              shlex.py
asynchat.py          ihooks.pyc             shlex.pyc
asynchat.pyc         imaplib.py             shutil.py
asyncore.py          imaplib.pyc            shutil.pyc
asyncore.pyc         imghdr.py              SimpleHTTPServer.py
atexit.py            imghdr.pyc             SimpleHTTPServer.pyc
atexit.pyc           imputil.py             SimpleXMLRPCServer.py
audiodev.py          imputil.pyc            SimpleXMLRPCServer.pyc
audiodev.pyc         inspect.py             site-packages
base64.py            inspect.pyc            site.py
base64.pyc           keyword.py             site.pyc
BaseHTTPServer.py    keyword.pyc            smtpd.py
BaseHTTPServer.pyc   lib-dynload            smtpd.pyc
Bastion.py           lib-tk                 smtplib.py
Bastion.pyc          LICENSE.txt            smtplib.pyc
bdb.py               linecache.py           sndhdr.py
bdb.pyc              linecache.pyc          sndhdr.pyc
binhex.py            locale.py              socket.py
binhex.pyc           locale.pyc             socket.pyc
bisect.py            logging                SocketServer.py
bisect.pyc           _LWPCookieJar.py       SocketServer.pyc
bsddb                _LWPCookieJar.pyc      sqlite3
calendar.py          macpath.py             sre_compile.py
calendar.pyc         macpath.pyc            sre_compile.pyc
CGIHTTPServer.py     macurl2path.py         sre_constants.py
CGIHTTPServer.pyc    macurl2path.pyc        sre_constants.pyc
cgi.py               mailbox.py             sre_parse.py
cgi.pyc              mailbox.pyc            sre_parse.pyc
cgitb.py             mailcap.py             sre.py
cgitb.pyc            mailcap.pyc            sre.pyc
chunk.py             markupbase.py          stat.py
chunk.pyc            markupbase.pyc         stat.pyc
cmd.py               md5.py                 statvfs.py
cmd.pyc              md5.pyc                statvfs.pyc
codecs.py            mhlib.py               StringIO.py
codecs.pyc           mhlib.pyc              StringIO.pyc
codeop.py            mimetools.py           stringold.py
codeop.pyc           mimetools.pyc          stringold.pyc
code.py              mimetypes.py           stringprep.py
code.pyc             mimetypes.pyc          stringprep.pyc
colorsys.py          MimeWriter.py          string.py
colorsys.pyc         MimeWriter.pyc         string.pyc
commands.py          mimify.py              _strptime.py
commands.pyc         mimify.pyc             _strptime.pyc
compileall.py        modulefinder.py        struct.py
compileall.pyc       modulefinder.pyc       struct.pyc
compiler             _MozillaCookieJar.py   subprocess.py
config               _MozillaCookieJar.pyc  subprocess.pyc
ConfigParser.py      multifile.py           sunaudio.py
ConfigParser.pyc     multifile.pyc          sunaudio.pyc
contextlib.py        mutex.py               sunau.py
contextlib.pyc       mutex.pyc              sunau.pyc
cookielib.py         netrc.py               symbol.py
cookielib.pyc        netrc.pyc              symbol.pyc
Cookie.py            new.py                 symtable.py
Cookie.pyc           new.pyc                symtable.pyc
copy.py              nntplib.py             tabnanny.py
copy.pyc             nntplib.pyc            tabnanny.pyc
copy_reg.py          ntpath.py              tarfile.py
copy_reg.pyc         ntpath.pyc             tarfile.pyc
cProfile.py          nturl2path.py          telnetlib.py
cProfile.pyc         nturl2path.pyc         telnetlib.pyc
csv.py               opcode.py              tempfile.py
csv.pyc              opcode.pyc             tempfile.pyc
ctypes               optparse.py            test
curses               optparse.pyc           textwrap.py
dbhash.py            os2emxpath.py          textwrap.pyc
dbhash.pyc           os2emxpath.pyc         this.py
decimal.py           os.py                  this.pyc
decimal.pyc          os.pyc                 _threading_local.py
difflib.py           pdb.doc                _threading_local.pyc
difflib.pyc          pdb.py                 threading.py
dircache.py          pdb.pyc                threading.pyc
dircache.pyc         __phello__.foo.py      timeit.py
dis.py               __phello__.foo.pyc     timeit.pyc
dis.pyc              pickle.py              toaiff.py
distutils            pickle.pyc             toaiff.pyc
doc                  pickletools.py         tokenize.py
doctest.py           pickletools.pyc        tokenize.pyc
doctest.pyc          pipes.py               token.py
DocXMLRPCServer.py   pipes.pyc              token.pyc
DocXMLRPCServer.pyc  pkgutil.py             traceback.py
dumbdbm.py           pkgutil.pyc            traceback.pyc
dumbdbm.pyc          platform.py            trace.py
dummy_threading.py   platform.pyc           trace.pyc
dummy_threading.pyc  plat-linux2            tty.py
dummy_thread.py      popen2.py              tty.pyc
dummy_thread.pyc     popen2.pyc             types.py
email                poplib.py              types.pyc
encodings            poplib.pyc             unittest.py
filecmp.py           posixfile.py           unittest.pyc
filecmp.pyc          posixfile.pyc          urllib2.py
fileinput.py         posixpath.py           urllib2.pyc
fileinput.pyc        posixpath.pyc          urllib.py
fnmatch.py           pprint.py              urllib.pyc
fnmatch.pyc          pprint.pyc             urlparse.py
formatter.py         pty.py                 urlparse.pyc
formatter.pyc        pty.pyc                UserDict.py
fpformat.py          pyclbr.py              UserDict.pyc
fpformat.pyc         pyclbr.pyc             UserList.py
ftplib.py            py_compile.py          UserList.pyc
ftplib.pyc           py_compile.pyc         user.py
functools.py         pydoc.py               user.pyc
functools.pyc        pydoc.pyc              UserString.py
__future__.py        Queue.py               UserString.pyc
__future__.pyc       Queue.pyc              uuid.py
getopt.py            quopri.py              uuid.pyc
getopt.pyc           quopri.pyc             uu.py
getpass.py           random.py              uu.pyc
getpass.pyc          random.pyc             warnings.py
gettext.py           repr.py                warnings.pyc
gettext.pyc          repr.pyc               wave.py
glob.py              re.py                  wave.pyc
glob.pyc             re.pyc                 weakref.py
gopherlib.py         rexec.py               weakref.pyc
gopherlib.pyc        rexec.pyc              webbrowser.py
gzip.py              rfc822.py              webbrowser.pyc
gzip.pyc             rfc822.pyc             whichdb.py
hashlib.py           rlcompleter.py         whichdb.pyc
hashlib.pyc          rlcompleter.pyc        wsgiref
heapq.py             robotparser.py         wsgiref.egg-info
heapq.pyc            robotparser.pyc        xdrlib.py
hmac.py              runpy.py               xdrlib.pyc
hmac.pyc             runpy.pyc              xml
hotshot              sched.py               xmllib.py
htmlentitydefs.py    sched.pyc              xmllib.pyc
htmlentitydefs.pyc   sets.py                xmlrpclib.py
htmllib.py           sets.pyc               xmlrpclib.pyc
htmllib.pyc          sgmllib.py             zipfile.py
HTMLParser.py        sgmllib.pyc            zipfile.pyc
HTMLParser.pyc       sha.py

```
This is mainly just to illustrate that the directory for lib-tk is in there, as it should be.
I'm completely stumped, then, regarding how to get Tk and qt python bindings to work in python2.5 without trying to build it from source.
I'd greatly appreciate it if anyone could offer me some advice.
Thanks.

Update: I used apt-get source --compile python2.5 to get the python source out of apt and compile it. I then installed all the packages separately using dpkg -i... and the problem persists. Interestingly, though, if I go into the the python build directory (either build-debug, build-shared, or build-static), and start the python executable located within that directory, then try importing _tkinter, it works. I still cannot import qt though.
If anyone has any advice, I would greately appreciate it.

Jake

---

