---
title: "Upgrade packages error... strange error..."
date: 2024-08-28
forum: Installation &amp; Upgrades
---

### Post by Goldengate01 on 2024-08-28
Hi guys hope you're doing great. Another day another update in the Linux world with a strange error indeed, troublesome perhaps? I post it because of this:

/usr/share/bleachbit/bleachbit/Windows.py:141: SyntaxWarning: invalid escape seq
uence '\ '
  msg = _('The file python3.dll was found in c:\ or c:\dlls, which indicates a p
ossible attempt at DLL search-order hijacking.')

The complete error:

```
fgonzalez@HP-255-G8-Notebook-PC:~$ sudo apt upgrade
Reading packages... Done
Creating dependencies tree... Done
Reading information state... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libcjson1 libavdevice60 ffmpeg libpostproc57 libavcodec60 libavutil58
  libswscale7 libswresample4 libavformat60 libavfilter9
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
Se actualizarán los siguientes paquetes:
  libpython3-dev libpython3-stdlib python3 python3-all python3-dev
  python3-distupgrade python3-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
9 updated, 0 new to install, 0 to delete y 0 no updated.
We need to download 258 kB of files.
It will be used 8.192 B of space...
¿Want to continue? [Y/n] Y
Des:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 libpython3-dev amd64 3.12.3-0ubuntu2 [10,3 kB]
Des:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 python3-dev amd64 3.12.3-0ubuntu2 [26,7 kB]
Des:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 python3-all amd64 3.12.3-0ubuntu2 [886 B]
Des:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 python3-minimal amd64 3.12.3-0ubuntu2 [27,4 kB]
Des:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 python3 amd64 3.12.3-0ubuntu2 [23,0 kB]
Des:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 libpython3-stdlib amd64 3.12.3-0ubuntu2 [10,0 kB]
Des:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 ubuntu-release-upgrader-gtk all 1:24.04.22 [9.070 B]
Des:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 ubuntu-release-upgrader-core all 1:24.04.22 [27,4 kB]
Des:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates/main amd64 python3-distupgrade all 1:24.04.22 [124 kB]
Downloaded 258 kB in 1s (242 kB/s)          
(Reading database ... 304886 files or directories.) --HERE PUT YOUR ENGLISH WORDS
Preparing to unpack .../libpython3-dev_3.12.3-0ubuntu2_amd64.deb ...
Unpacking libpython3-dev:amd64 (3.12.3-0ubuntu2) sobre (3.12.3-0ubuntu1) .
..
Preparing to unpack  .../python3-dev_3.12.3-0ubuntu2_amd64.deb ...
Unpacking python3-dev (3.12.3-0ubuntu2) over (3.12.3-0ubuntu1) ...
Preparing to unpack  .../python3-all_3.12.3-0ubuntu2_amd64.deb ...
Unpacking python3-all (3.12.3-0ubuntu2) over (3.12.3-0ubuntu1) ...
Preparing to unpack  .../python3-minimal_3.12.3-0ubuntu2_amd64.deb ...
Unpacking python3-minimal (3.12.3-0ubuntu2) over (3.12.3-0ubuntu1) ...
Configuring python3-minimal (3.12.3-0ubuntu2) ...
(Reading database ... 304886 files installed.)
Preparing to unpack  .../python3_3.12.3-0ubuntu2_amd64.deb ...
running python pre-rtupdate hooks for python3.12...
Unpacking python3 (3.12.3-0ubuntu2) sobre (3.12.3-0ubuntu1) ...
Preparing to unpack .../libpython3-stdlib_3.12.3-0ubuntu2_amd64.deb ..
.
Unpacking libpython3-stdlib:amd64 (3.12.3-0ubuntu2) over (3.12.3-0ubuntu1
) ...
Preparing to unpack  .../ubuntu-release-upgrader-gtk_1%3a24.04.22_all.d
eb ...
Unpacking ubuntu-release-upgrader-gtk (1:24.04.22) over (1:24.04.19) ...
Preparing to unpack  .../ubuntu-release-upgrader-core_1%3a24.04.22_all.
deb ...
Preparing to unpack  ubuntu-release-upgrader-core (1:24.04.22) over (1:24.04.19) ...
Preparing to unpack .../python3-distupgrade_1%3a24.04.22_all.deb ...
Unpacking python3-distupgrade (1:24.04.22) sobre (1:24.04.19) ...
Configuring libpython3-dev:amd64 (3.12.3-0ubuntu2) ...
Configuring libpython3-stdlib:amd64 (3.12.3-0ubuntu2) ...
Configuring python3 (3.12.3-0ubuntu2) ...
running python rtupdate hooks for python3.12...
/usr/share/bleachbit/bleachbit/Action.py:42: SyntaxWarning: invalid escape seque
nce '\['
  return re.search('[?*\[\]]', s) is not None
/usr/share/bleachbit/bleachbit/Cleaner.py:402: SyntaxWarning: invalid escape seq
uence '\W'
  '$LocalAppData\\Microsoft\\Windows\WER\\ReportQueue\\*\\*',
/usr/share/bleachbit/bleachbit/Cleaner.py:419: SyntaxWarning: invalid escape seq
uence '\F'
  '$windir\\Microsoft.NET\Framework\*\*.log',
/usr/share/bleachbit/bleachbit/Cleaner.py:432: SyntaxWarning: invalid escape seq
uence '\E'
  '$windir\\system32\\LogFiles\\WMI\\RTBackup\EtwRT.*etl',
/usr/share/bleachbit/bleachbit/Memory.py:67: SyntaxWarning: invalid escape seque
nce '\w'
  ret = re.search('^swapoff (\w* )?(/[\w/.-]+)$', swapoff)
/usr/share/bleachbit/bleachbit/Memory.py:159: SyntaxWarning: invalid escape sequ
ence '\s'
  if not re.search('Filename\s+Type\s+Size', line):
/usr/share/bleachbit/bleachbit/Memory.py:162: SyntaxWarning: invalid escape sequ
ence '\s'
  ret = re.search("%s\s+\w+\s+([0-9]+)\s" % device, line)
/usr/share/bleachbit/bleachbit/Unix.py:67: SyntaxWarning: invalid escape sequenc
e '\.'
  """Adds a filter consisting of a prefix and a postfix
/usr/share/bleachbit/bleachbit/Unix.py:652: SyntaxWarning: invalid escape sequen
ce '\.'
  paths = re.findall('/[/a-z\.\*]+', stdout)
/usr/share/bleachbit/bleachbit/Unix.py:720: SyntaxWarning: invalid escape sequen
ce '\d'
  cregex = re.compile("Freed space: ([\d.]+[\s]+[BkMG])")
/usr/share/bleachbit/bleachbit/Windows.py:21: SyntaxWarning: invalid escape sequ
ence '\S'
  """
/usr/share/bleachbit/bleachbit/Windows.py:141: SyntaxWarning: invalid escape seq
uence '\ '
  msg = _('The file python3.dll was found in c:\ or c:\dlls, which indicates a p
ossible attempt at DLL search-order hijacking.')
/usr/share/bleachbit/bleachbit/Windows.py:157: SyntaxWarning: invalid escape seq
uence '\g'
  for fn in glob.glob(os.path.expandvars('%TEMP%\gdbus-nonce-file-*')):
/usr/share/gdebi/GDebi/GDebiCli.py:159: SyntaxWarning: invalid escape sequence '
\S'
  c = findall("[[(](\S+)/\S+[])]", msg)[0].lower()
/usr/share/hplip/base/imagesize.py:186: SyntaxWarning: invalid escape sequence '
\#'
  re.compile('\#define\s+\S+\s+\d+')     : ('image/x-xbitmap', xbmsize),
/usr/share/hplip/base/imagesize.py:187: SyntaxWarning: invalid escape sequence '
\/'
  re.compile('\/\* XPM \*\/')            : ('image/x-xpixmap', xpmsize),
/usr/share/hplip/base/imagesize.py:189: SyntaxWarning: invalid escape sequence '
\*'
  re.compile('^II\*\x00')                : ('image/tiff', tiffsize),
/usr/share/hplip/fax/ledmfax.py:46: SyntaxWarning: invalid escape sequence '\d'
  http_result_pat = re.compile(b"""HTTP/\d.\d\s(\d+)""", re.I)
/usr/lib/rhythmbox/plugins/alternative-toolbar/alttoolbar_plugins.py:171: Syntax
Warning: invalid escape sequence '\('
  translation = re.sub('\(..\)', '', translation, flags=re.DOTALL)
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/AstrawebParser.py:64: SyntaxWarning: invalid escape sequence '\/'
  url = re.split('(\/display[^"]*)', entry)[1]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/AstrawebParser.py:66: SyntaxWarning: invalid escape sequence '\/'
  title = re.split('(\/display[^>]*)([^<]*)', entry)[2][1:].strip()
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/AstrawebParser.py:97: SyntaxWarning: invalid escape sequence '\/'
  lyrics = re.split('(<font face=arial size=2>)(.*)(<\/font><br></td><td*)', result)[2]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/JetlyricsParser.py:50: SyntaxWarning: invalid escape sequence '\.'
  m = re.search('<a href=\'([http://jetlyrics\.com/viewlyrics\.php\?id=](http://jetlyrics\.com/viewlyrics\.php\?id=)[0-9]*)\'>', result)
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/JlyricParser.py:49: SyntaxWarning: invalid escape sequence '\.'
  m = re.search('<div class=\'title\'><a href=\'(/artist/[^\.]*\.html)\'>', result)
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/TerraParser.py:39: SyntaxWarning: invalid escape sequence '\w'
  pattern = re.compile("&(#?\w+?);")
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/WinampcnParser.py:87: SyntaxWarning: invalid escape sequence '\['
  lrcplaintext = re.sub('\[.*?\]', '', lrcplaintext)
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/lyrics.py:44: SyntaxWarning: invalid escape sequence '\('
  LYRIC_TITLE_STRIP=["\(live[^\)]*\)", "\(acoustic[^\)]*\)", "\([^\)]*mix\)", "\([^\)]*version\)", "\([^\)]*edit\)", "\(feat[^\)]*\)"]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/lyrics.py:44: SyntaxWarning: invalid escape sequence '\('
  LYRIC_TITLE_STRIP=["\(live[^\)]*\)", "\(acoustic[^\)]*\)", "\([^\)]*mix\)", "\([^\)]*version\)", "\([^\)]*edit\)", "\(feat[^\)]*\)"]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/lyrics.py:44: SyntaxWarning: invalid escape sequence '\('
  LYRIC_TITLE_STRIP=["\(live[^\)]*\)", "\(acoustic[^\)]*\)", "\([^\)]*mix\)", "\([^\)]*version\)", "\([^\)]*edit\)", "\(feat[^\)]*\)"]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/lyrics.py:44: SyntaxWarning: invalid escape sequence '\('
  LYRIC_TITLE_STRIP=["\(live[^\)]*\)", "\(acoustic[^\)]*\)", "\([^\)]*mix\)", "\([^\)]*version\)", "\([^\)]*edit\)", "\(feat[^\)]*\)"]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/lyrics.py:44: SyntaxWarning: invalid escape sequence '\('
  LYRIC_TITLE_STRIP=["\(live[^\)]*\)", "\(acoustic[^\)]*\)", "\([^\)]*mix\)", "\([^\)]*version\)", "\([^\)]*edit\)", "\(feat[^\)]*\)"]
/usr/lib/x86_64-linux-gnu/rhythmbox/plugins/lyrics/lyrics.py:44: SyntaxWarning: invalid escape sequence '\('
  LYRIC_TITLE_STRIP=["\(live[^\)]*\)", "\(acoustic[^\)]*\)", "\([^\)]*mix\)", "\([^\)]*version\)", "\([^\)]*edit\)", "\(feat[^\)]*\)"]
running python post-rtupdate hooks for python3.12...
Configuring python3-distupgrade (1:24.04.22) ...
Configuring python3-dev (3.12.3-0ubuntu2) ...
Configuring ubuntu-release-upgrader-core (1:24.04.22) ...
Configuring ubuntu-release-upgrader-gtk (1:24.04.22) ...
Configuring python3-all (3.12.3-0ubuntu2) ...
Processing triggers doc-base (0.11.2) ...
Processing 1 file doc-base changed...
Processing triggers man-db (2.12.0-4build2) ...
fgonzalez@HP-255-G8-Notebook-PC:~$ 

```

Should I have to worry?

Regards

Fran

---

### Post by stephan4 on 2024-08-28
Dude ...

Use English in your output and, for god&#8217;s sake, please format it in a monospaced font.
Eyecancer is bad!

---

### Post by Goldengate01 on 2024-08-28
Done.. anyway the error in the post is in english lang.

Regards 

Fran

---

### Post by corradoventu on 2024-08-28
In a recent version of Python (3.12?) backslashes in regular expressions need to get quoted or the expressions defined as raw strings (r'...'). Could you change it that way? Using raw strings should not break older versions of Python.
[https://stackoverflow.com/questions/77531208/python3-12-syntaxwarning-on-triplequoted-string-d-must-be-d](https://stackoverflow.com/questions/77531208/python3-12-syntaxwarning-on-triplequoted-string-d-must-be-d)
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/2054869](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/2054869)
[https://bugs.launchpad.net/hplip/+bug/2029480](https://bugs.launchpad.net/hplip/+bug/2029480)

---

### Post by Goldengate01 on 2024-08-28
Thx! I'm checking the links you provided! 

Have a great day!

Fran

---

### Post by nbushman on 2024-08-28
I'm seeing a similar "SyntaxWarning: invalid escape sequence" error.

Here are the relevant lines from my "sudo apt upgrade" output:

[FONT=courier new]
[/FONT]```
[FONT=courier new]Setting up python3 (3.12.3-0ubuntu2) ...[/FONT]
[FONT=courier new]running python rtupdate hooks for python3.12...[/FONT]
[FONT=courier new]/usr/share/hplip/base/imagesize.py:186: SyntaxWarning: invalid escape sequence '[/FONT]
[FONT=courier new]\#'[/FONT]
[FONT=courier new]  re.compile('\#define\s+\S+\s+\d+')     : ('image/x-xbitmap', xbmsize),[/FONT]
[FONT=courier new]/usr/share/hplip/base/imagesize.py:187: SyntaxWarning: invalid escape sequence '[/FONT]
[FONT=courier new]\/'[/FONT]
[FONT=courier new]  re.compile('\/\* XPM \*\/')            : ('image/x-xpixmap', xpmsize),[/FONT]
[FONT=courier new]/usr/share/hplip/base/imagesize.py:189: SyntaxWarning: invalid escape sequence '[/FONT]
[FONT=courier new]\*'[/FONT]
[FONT=courier new]  re.compile('^II\*\x00')                : ('image/tiff', tiffsize),[/FONT]
[FONT=courier new]/usr/share/hplip/fax/ledmfax.py:46: SyntaxWarning: invalid escape sequence '\d'[/FONT]
[FONT=courier new]  http_result_pat = re.compile(b"""HTTP/\d.\d\s(\d+)""", re.I)[/FONT]
[FONT=courier new]running python post-rtupdate hooks for python3.12...
[/FONT]
```

My system info:

# System Details Report
---


## Report details
- **Date generated:**                              2024-08-28 20:03:16


## Hardware Information:
- **Hardware Model:**                              Dell Inc. XPS 13 9360
- **Memory:**                                      16.0 GiB
- **Processor:**                                   Intel® Core™ i7-7560U × 4
- **Graphics:**                                    Intel® Iris® Plus Graphics 640 (Kaby Lake GT3e) (KBL GT3)
- **Disk Capacity:**                               (null)


## Software Information:
- **Firmware Version:**                            2.21.0
- **OS Name:**                                     Ubuntu 24.04.1 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.8.0-41-generic

---

