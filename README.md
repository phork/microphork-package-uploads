#microphork

* [By Phork Labs](http://phorklabs.com/)
* Version: 0.1


##Introduction

This is a file uploader package for the microphork framework. It validates and saves files uploaded via POST.


##Usage

```
//print a simple upload form
\Phork::output()->addContent('
    <form enctype="multipart/form-data" method="post">
        <input name="upload" type="file" />
        <button type="submit">submit</button>
    </form>
');

//load and alias a new uploads package
class_alias(\Phork::instance()->initPackage('Uploads'), 'PhorkUploads');

//if a file was uploaded then save it
if (\Phork::router()->getMethod() == 'post' && $files = \PhorkUploads::getFiles()) {
    if (!empty($files['upload']) && $file = $files['upload']) {
    
        //uploaded $file['name'] to $file['tmp_name'] and move it to $output
        \PhorkUploads::saveFile($file['tmp_name'], $output = LOG_PATH.'upload.demo', true);
    }
}
```


##License

Licensed under The MIT License
<http://www.opensource.org/licenses/mit-license.php>