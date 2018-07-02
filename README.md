
# VITOMUCI [![npm version](https://badge.fury.io/js/vitomuci.svg)](https://badge.fury.io/js/vitomuci) [![Build Status](https://travis-ci.org/jufabeck2202/vitomuci.svg?branch=master)](https://travis-ci.org/jufabeck2202/vitomuci)
![](https://raw.githubusercontent.com/jufabeck2202/vitomuci/master/screenshot.svg)

**Vitomuci** is a video to mp3 converter that splits the video file into small audio clips and combines them into one album with a generated cover. It is also possible to download videos and playlists directly and split them into clips.
It is inspired by the [sub2srs](http://subs2srs.sourceforge.net/#extract_audio) extract Audio from Media Tool.
## Installation
Install **Vitomuci** globally

```shell
npm install -g vitomuci
```
## Usage
```shell
  Usage: vitomuci [options] <directory/file/yt> <output dir(only when dowloading from yt)>

  Options:

    -V, --version              output the version number
    -s, --start [start]        in s: cut away start from the beginning to remove advertisment etc. (default: 18)
    -e, --end [end]            in s: cut away end from the end to remove advertisment etc. (default: 18)
    -d, --duration [duration]  the duration of the clips the file gets split to (default: 18)
    -n, --name [name]          the name of the clips and metadata (default: null)
    -c, --cover                if a cover photo should be added to the mp3 metadata
    -m, --metadata             adds metadata to all generated clips to combine them to one album
    -r, --rename               removes text inside brackets to cleanup filenames like (1080p)
    -h, --help                 output usage information
```
### Make audio clips for all files inside a folder:
```shell
vitomuci /videos/
```
### Make audio clips for all files matching a regex string:
```shell
vitomuci  /videos/terrace house Episode??.mp4
```

### Download a YouTube video and split it into audio clips:
```shell
vitomuci  https://www.youtube.com/watch?v=Qrli6PxgxFM Desktop/
```
### Download a YouTube playlist and split it into audio clips:
```shell
vitomuci  https://www.youtube.com/playlist?list=PLuf9JIUOHQ-NC98LUExv1WWl4mwPXzwnI Desktop/
```
**When downloading YouTube videos an output path is required:** 
```shell
vitomuci <ytlink> <output folder>

```
vitomuci will create a YouTube folder and keep the downloaded .mp4 files 

## Options
**-s, --start [start]:** Seconds you want to skip from the beginning of a a file. -s 60 will skip the first 60 seconds of a file before creating mp3 clips. Useful when you want to remove intros or openings.

**-s, --start [start]:** Seconds you want to skip from the end of a a file. -e 60 will skip the last 60 seconds of a file. Useful when you want to remove outros or endings.

**-d, --duration [duration]:** the duration of the audio clips. Default: 3 min.

** -m, --metadata:** Adds album, artist and disc metadata to cobine all clips into one album. Usefull if you want the clips to show up as one album and not one album per clip. Default: false

**-n, --name [name]:** name of to album for the clips. Default: Name of first file. **Requires -metadata to be set**

**-c, --cover:** Takes a picture and use it as cover for the generated album. Default: false. **Requires -metadata to be set**

**-r, --rename:** Removes text inside brackets to cleanup filenames. Removes brackets like (1080p60) or [Japanese]. 


## Examples
```shell
vitomuci -s 30 -e 30 -d 60 -c -m /videos/testvideoPart*.mp4
```
Convert all videos files matching the regex "testvideoPart*.mp4" to mp3 and split them into 1 minute long parts, skipping the first 30 and last 30 seconds.Add metadata and a cover picture, combine them into one album. Audio clips will be saved under *videos/audio*

```shell
vitomuci -d 120 https://www.youtube.com/playlist?list=PLWKjhJtqVAbnZtkAI3BqcYxKnfWn_C704 desktop/
```
Download all videos from the YouTube playlist, split them into 2 minute parts.

```shell
vitumici -d 20 -r /videos/
```
Renames all video files inside the videos folder, remove strings like (1080p60) or [Japanese] and splits the renamed files into 20s clips.
