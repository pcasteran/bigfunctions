---
hide:
  - navigation
---

#
<img src="../assets/logo_and_name.png" alt="drawing" width="300"/>

BigFunctions are public BigQuery routines that give you new *SQL powers* in BigQuery 💪.

We are introducing today the first two functions. [Tell us what you think](https://github.com/unytics/bigfunctions/discussions)! 😊.

---


## chart

> Replaces the variables surrounded by brackets such as `{{variable_name}}` in `template` by their values defined in `context`.
> Beware that `context` keys and string values must be surrounded by double-quotes `"` and not single-quotes `'`.
```
chart(data, chart_type, ylabel)
```
> **Returns** ➜ `STRING`

<h3>Example</h3>


=== "EU"

    ``` sql
    SELECT bigfunctions.eu.chart([
      ('2022-08-01', 10000),
      ('2022-08-02', 20000),
      ('2022-08-03', 40000),
      ('2022-08-04', 80000)
    ], 'bar', 'sales') as html
    ```

=== "US"

    ``` sql
    SELECT bigfunctions.us.chart([
      ('2022-08-01', 10000),
      ('2022-08-02', 20000),
      ('2022-08-03', 40000),
      ('2022-08-04', 80000)
    ], 'bar', 'sales') as html
    ```

=== "europe-west1"

    ``` sql
    SELECT bigfunctions.europe_west1.chart([
      ('2022-08-01', 10000),
      ('2022-08-02', 20000),
      ('2022-08-03', 40000),
      ('2022-08-04', 80000)
    ], 'bar', 'sales') as html
    ```

=== "your-region2"

    ``` sql
    SELECT bigfunctions.your_region2.chart([
      ('2022-08-01', 10000),
      ('2022-08-02', 20000),
      ('2022-08-03', 40000),
      ('2022-08-04', 80000)
    ], 'bar', 'sales') as html
    ```


<a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/chart.yaml" target="_blank">Source Code</a>

---




## chart_query_result

> Show a chart
```
chart(query, chart_type)
```
> **Returns** ➜ `html STRING`

<h3>Example</h3>

code
cd

<a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/chart_query_result.yaml" target="_blank">Source Code</a>

---




## explore_column

> Returns statistics about column
```
explore_column(fully_qualified_column, output)
```
> **Returns** ➜ `output JSON`, `output_html STRING`

<h3>Example</h3>


=== "EU"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.eu.explore_column('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```

=== "US"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.us.explore_column('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```

=== "europe-west1"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.europe_west1.explore_column('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```

=== "your-region2"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.your_region2.explore_column('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```


<a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/explore_column.yaml" target="_blank">Source Code</a>

---




## explore_dataset

> Returns infos about dataset tables as a json output
```
explore_dataset(fully_qualified_dataset, output)
```
> **Returns** ➜ `output JSON`, `output_html STRING`

<h3>Example</h3>


=== "EU"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.eu.explore_dataset('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```

=== "US"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.us.explore_dataset('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```

=== "europe-west1"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.europe_west1.explore_dataset('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```

=== "your-region2"

    ``` sql
    DECLARE output JSON;
    DECLARE output_html string;
    CALL bigfunctions.your_region2.explore_dataset('bigquery-public-data.samples', output, output_html);
    SELECT output;
    SELECT output_html;
    
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | table_catalog        | table_schema | table_name      | table_type | is_insertable_into | is_typed | creation_time            | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    | bigquery-public-data | samples      | natality        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:47.183Z | ... |
    | bigquery-public-data | samples      | github_timeline | BASE TABLE | YES                | NO       | 2016-03-14T17:16:45.074Z | ... |
    | bigquery-public-data | samples      | github_nested   | BASE TABLE | YES                | NO       | 2016-03-14T17:16:44.113Z | ... |
    | bigquery-public-data | samples      | trigrams        | BASE TABLE | YES                | NO       | 2016-03-14T17:16:50.399Z | ... |
    | ...                  | ...          | ...             | ...        | ...                | ...      | ...                      | ... |
    +----------------------+--------------+-----------------+------------+--------------------+----------+--------------------------+-----+
    ```


<a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/explore_dataset.yaml" target="_blank">Source Code</a>

---




## levenshtein

> Replaces the variables surrounded by brackets such as `{{variable_name}}` in `template` by their values defined in `context`.
> Beware that `context` keys and string values must be surrounded by double-quotes `"` and not single-quotes `'`.
```
levenshtein(template, context)
```
> **Returns** ➜ `INT64`

<h3>Example</h3>


=== "EU"

    ``` sql
    SELECT bigfunctions.eu.levenshtein('back', 'book') as distance;
    
    +-------------+
    | distance    |
    +-------------+
    | 2           |
    +-------------+
    ```

=== "US"

    ``` sql
    SELECT bigfunctions.us.levenshtein('back', 'book') as distance;
    
    +-------------+
    | distance    |
    +-------------+
    | 2           |
    +-------------+
    ```

=== "europe-west1"

    ``` sql
    SELECT bigfunctions.europe_west1.levenshtein('back', 'book') as distance;
    
    +-------------+
    | distance    |
    +-------------+
    | 2           |
    +-------------+
    ```

=== "your-region2"

    ``` sql
    SELECT bigfunctions.your_region2.levenshtein('back', 'book') as distance;
    
    +-------------+
    | distance    |
    +-------------+
    | 2           |
    +-------------+
    ```


<a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/levenshtein.yaml" target="_blank">Source Code</a>

---




## render_string

> Replaces the variables surrounded by brackets such as `{{variable_name}}` in `template` by their values defined in `context`.
> Beware that `context` keys and string values must be surrounded by double-quotes `"` and not single-quotes `'`.
```
render_string(template, context)
```
> **Returns** ➜ `STRING`

<h3>Example</h3>


=== "EU"

    ``` sql
    SELECT bigfunctions.eu.render_string('Hello {{username}}', '{"username": "James"}') as rendered_content;
    
    +-------------+
    | rendered_content     |
    +-------------+
    | Hello World |
    +-------------+
    ```

=== "US"

    ``` sql
    SELECT bigfunctions.us.render_string('Hello {{username}}', '{"username": "James"}') as rendered_content;
    
    +-------------+
    | rendered_content     |
    +-------------+
    | Hello World |
    +-------------+
    ```

=== "europe-west1"

    ``` sql
    SELECT bigfunctions.europe_west1.render_string('Hello {{username}}', '{"username": "James"}') as rendered_content;
    
    +-------------+
    | rendered_content     |
    +-------------+
    | Hello World |
    +-------------+
    ```

=== "your-region2"

    ``` sql
    SELECT bigfunctions.your_region2.render_string('Hello {{username}}', '{"username": "James"}') as rendered_content;
    
    +-------------+
    | rendered_content     |
    +-------------+
    | Hello World |
    +-------------+
    ```


<a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/render_string.yaml" target="_blank">Source Code</a>

---
