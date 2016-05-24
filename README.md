cyg-pall
=======

cyg-pall is an advanced version of apt-cyg, command-line installer for [Cygwin](http://cygwin.com/) which cooperates with Cygwin Setup and uses the same repository. 

Supporting pre-resolving dependencies and parallel-downloading, cyg-pall works faster than apt-cyg.

The syntax is similar to apt-get. Usage examples:

* "cyg-pall install &lt;package names&gt;" to install packages
* "cyg-pall resume-install" to resume interrupted installing
* "cyg-pall remove &lt;package names&gt;" to remove packages
* "cyg-pall update" to update setup.ini
* "cyg-pall show" to show installed packages
* "cyg-pall find &lt;pattern(s)&gt;" to find packages matching patterns
* "cyg-pall describe &lt;pattern(s)&gt;" to describe packages matching patterns
* "cyg-pall packageof &lt;commands or files&gt;" to locate parent packages
* "cyg-pall pathof &lt;cache|mirror|mirrordir|cache/mirrordir&gt;" to show path"

Requirements
-----------

cyg-pall requires the cygwin default environment and optional packages below.

* aria2

Quick start
-----------

cyg-pall is a simple script. Once you have a copy, make it executable:

    # chmod +x /bin/cyg-pall

Optionally place cyg-pall in a bin/ folder on your path.

Then use cyg-pall, for example:

    # cyg-pall install vim

New features
------------

### Parallel downloading with aria2

Aria2 is an advances file downloading tool that allows you to download files with faster speed.

cyg-pall provides multi-connection downloading using aria2.

You can change the maximum number of connections with the ```--max-connections``` option.

### True multi-architecture support

Let think a case that you want to install the x86 package when you are working under the x86_64 environment.
For example:

    # cyg-pall --charch x86 install chere

As of 2013-10-26, chere package is provided for only the repository for x86.

Remarks:
Of course, you must install both environments of x86_64 and x86, beforehand.

### Pre-resolving dependencies

cyg-pall finds all depending packages before downloading and installing.

### Check dependency on removing

You can remove all packages depending on packages you want to remove.

### Resume installation when downloading fails

Type ```cyg-pall resume-install``` to resume interrupted downloading.

You don't need to be annoy with an unstable internet connection...

### Force re-install packages

You can reinstall a package by using ```cyg-pall --force install <package>```

### Rapid mode

If you are hurrying to install some packages, use ```--rapid``` to avoid wasting time 
by updating setup.ini, checking certificates, checking signatures, checking MD5s, etc.

