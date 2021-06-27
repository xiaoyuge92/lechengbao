##### 1、nginx日志问题
```
思路是将日志读取到nginx_log表
表字段
id, domain, status, date, others

select round(s_num / total, 3) from (
    select * from (select count(1) total from nginx_log 
    where date = 'xx' and demain = 'xx') t1 
    inner join (
    select count(1) as s_num from nginx_log 
    where date = 'xx' and demain = 'xx' and status = 'ok') t2 
    on 1 = 1) t

```



##### 2、编写sql查询，查询有多少用户在2020年9月开启关卡数大于等于1000 小于等于2000

```
select count(1) from (
    select user_id,count(1) as count from event_log 
    where event_timestamp >= unix_timestamp('2020-09-01') and 
    event_timestamp < unix_timestamp('2020-10-01') 
    group by user_id) t 
where count >= 1000 and count < 2000;
```

##### 3、国际象棋模型
```
    
数据表设计如下：

clubs (俱乐部表)

id , name(名称）, adress（地址）, others （其他）

members (会员表)

id, p_id (棋手id), c_id(俱乐部id), others

players （棋手表）

id, p_name（棋手名称）, address（地址）,  m_id (关联会员id)), ranking(排名), others

tournaments (锦标赛表)

id, name (锦标赛名称) start_time(开始时间）, end_time（结束时间）, others

tournaments_dtl（锦标赛详情表）
id, t_id(锦标赛id), sponsor_name(赞助商名称） , others


matches (比赛表)

id, t_id(锦标赛id), nums（场次） p_id (棋手id), others

```
